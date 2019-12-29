## Quantum Programming 101

> We have a task, make something accurate and reliable out of something that is fundamentally chaotic.

***NOTE: [Click Here](#quantum-random-number-generator) to skip Theory and start quantum programming now..***

Quantum Computers are the next-generation computers that will enhance the power and efficiency of computers that we use at home. Through this series of blogs or possibly if I gather enough motivation, a series of videos, I will be documenting my journey into the development of software that utilizes the power of quantum computers.

Before jumping into the programming bit, we must take some time and understand how quantum computers are different from classical computers (the one you are reading this blog, as of the year 2020 --- anything can happen in the future).

## Classical Computers
All of these computers fundamentally function in the same way, there is a switch and you can turn this switch on and off. If the switch is off, then that is represented by 0 and if the switch is on, then that is represented by a 1.

By combining an infinite number of switches, we can, in theory, solve any problem there is provided we have infinite time.

In addition to these bits, we have logic gates that help us to manipulate these bits, like do mathematical operations on them. Some of the logic gates in classical computers are:

**AND Gate**: These types of gates take two bits as inputs and 1 bit as Output.

| A | B | Out |
|---|---|:---:|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

You can see in the above table, that an AND gate only returns a 1 if both the inputs are 1.

**OR Gate**: These gates are similar to AND gates but it returns a 1 if any of the input is 1.

| A | B | Out |
|---|---|:---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

**NOT Gate**: These gates just flip the input.

| A | Out |
|---|:---:|
| 1 | 0 |
| 0 | 1 |

We can also mix these three basic gates to make gates like XOR, NAND, NOR, etc and using these gates we can make a circuit that can add two numbers, which is another field of computer engineering that is out of the scope of this post. Let's talk about Quantum Computers.

## Quantum Computers
In classical computing we know exactly what is the state of the switches, it will be either on or off and nothing in between. In Quantum Computers, the thing gets a little weird because, in this type of computers, the switch can be simultaneously both on and off. And this special property of QC (Quantum Computers) along with few more which we will talk about in a bit is the reason why these computers are so fast.

Another great thing about QC is that it used a Quantum Bits (Qubits) to represent its internal state (comparable to a bit in classical computers) and for this reason, **a quantum computer can hold 2^n bits worth of information with just n qubits**

Now let's talk about some quantum mechanical concepts that are useful in Quantum Computing.

### Spin
After Shrodinger wrote his famous equation and everything seems to be working in quantum mechanics some scientists noticed that some particles interact with the surrounding magnetic field and the source of this behaviour of a quantum particle was labelled **spin**.

You can watch this video by the youtube channel  [Looking Glass Universe](https://www.youtube.com/watch?v=cd2Ua9dKEl8)  to get an intuition of what spin is.

Spin is actually a misnomer, the particles don't actually spin around some axis and nobody really knows how this property of a quantum particle works but for now we are defining spin like we defined Energy or Charge, simple English and mathematical equations, **Spin is a property that is responsible for a particle to act as Magnets**.

For the next section of this blog remember that any quantum particle has two base states:
1. **Spin Down**: This is the least energy state represented as a 0 in Quantum Computing.
2. **Spin Up**: This is the highest energy state represented as a 1.

### Superposition
Superposition in quantum mechanics is a very deep subject, just watch this  [video](https://www.youtube.com/watch?v=YB4uqpQd2AQ)  to get an intuition of what it is. Basically, **superposition is a special situation where a particle is both Spin Up and Spin Down and also any combination of those**.

Point to remember in Quantum Computing: when you measure a particle that is in superposition, it will be collapsed to one of the base states either spin-up or spin-down.

### Entanglement
ELI5 Version: There are two particles that are connected together when we put these particles in Superposition and separate them by great distance like 100,000 light-years apart (hypothetically) and measure one of them, and you find that it is, let's say, spin-up state and then measure the second particle,  it will most likely collapse to spin-down state and vice versa.

If you want to know the mathematics behind Entanglement, just watch this  [video](https://www.youtube.com/watch?v=-WSWz1H3mJg).

---

# Quantum Random Number Generator
Enough of the theory, let's do some actual programming. I will be posting a new blog that explains most of the Quantum Gates in detail.

Throughout this series, I will be using Google's Cirq quantum programming framework, if you want to use IBM's Qiskit then you can follow their documentation but all of the concepts and algorithms are same.

### Installing Cirq.
Assuming that you have the latest version of Python and PIP installed.

```
pip install cirq
```
This line should install all of the dependencies and the Cirq framework itself.

Then open your Code Editor of choice, open a new python file and import cirq (I'll me aliasing as c)

### Start coding

```
import cirq as c
```
In Cirq, there are two types of Qubit objects that you can use.
1. **GridQubit**: This will allocate you a Qubit in a 2D lattice of a Quantum Device.
2. **LineQubit**: This will allocate you a qubit in a 1D line.

Which object you have to use will depend on the Architecture of the Quantum Device. Most Quantum Computers I've seen uses a Grid Architecture so I always stick to GridQubits.

In order to get a Qubit in cirq, use this line of code.

```
qubits = [c.GridQubit(0,0)]
```
Here 0,0 is the position of a qubit in the Chip. Since quantum computing is a relatively new field of computer science we have to work closely with Quantum Hardware. So you have to make sure that this qubit is available in the device you are using.

For example, if you are using Google's Bristlecone quantum chip, then you can print the placement of qubits in this device using:

```
print(c.google.devices.Bristlecone)
```
*Side Note: I am planning in future, I will make a quantum programming language and compiler that will be aware of this nitty-gritty and allocate qubits as required. I will be documenting that process too so, make sure to follow my blog xD*

Next, we have to initialize a Quantum Circuit.
```
device = c.google.devices.Bristlecone
circuit = c.Circuit(device=device)
```
In this, the device attribute specifies which Quantum Device you will be using. If you leave this blank, then cirq will automatically create an architecture for you based in your circuit. But you will not be able to run it on an actual Quantum Computer, cirq will make a simulated quantum computer in your local computer.

*Side Note 2: Cirq currently offers Google's quantum devices and access to there Quantum Computer is invite-only. IBM is so much better than Google in terms of this. Then why don't you use Qiskit Tanseer? I tried but Qiskit is not installing on my Linux machine, some issue with gcc that I can't figure out nor there is any solution on the Internet :( so I'm stuck with Cirq.*
 
Now it's time to do some operations on the Qubit we've created and it's time to introduce two quantum gates.

Before that, let's initialize some variables.
```
# H ---> A list of all Hadamard gates
# T ---> A list of all Moments in the circuit
# M ---> A list of all Measurement gates
H,T,M = [],[],[]
```
**Hadamard Gate (H)**: This gate is used to put a qubit in a superposition state.

In code, you can do something like this.
```
for qubit in qubits:
    H.append(c.H(qubit))
```

**Measurement Gate**: This gate is used to collapse the superposition and measure the resultant state.

```
for qubit in qubits:
    M.append(c.measure(qubit))
```
Now, we arrange these gates in different Moments, A Moment in quantum computing is a timestamp. If you want to execute more than one instruction at the same time then put that in the same Moment.

```
# First we put the qubits in superposition
# then we measure them
T = [H,M]
```
Finally, add the Moments in the circuit that we created in the beginning.

```
circuit.append(T)
print(circuit)
```
The print statement will display the outline of the circuit with different gates.

Next step is to run this circuit on a Quantum Computer. Since Google does not allow me or anyone uninvited to use their device, we have to simulate a Bristlecone device on our computer.

```
# Initialise a Quantum Simulator
# (Can be replaced by an actual Quantum Computer) 
qsim = c.Simulator()
```
And finally, this function will take an integer `n` and output an `n bit` number

```
def getRandomNumber(n=8):
    result = ""
    for _ in range(n):
        
        # Run the circuit in a Quantum Computer
        # using this line of code.
        r = qsim.run(circuit, repetitions=1)
        
        for key in r.data:
            data = r.data[key].value_counts()
            cbit = data.head(1).keys()[0]
            result += str(cbit)
    
    # Convert binary to integer
    return int(result,2)
```

Obviously, this program does not demonstrate the advantage of exponential computational power of a Quantum Computer but this is a great starting point to the universe of Quantum Programming.

Thank You.