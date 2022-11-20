Run Jupyter

```bash
pip install jupyterlab
jupiter-lab
```

install requirements within the notebook:
```bash
%pip install numpy
%pip install qiskit
%pip install matplotlib
```

examples:
```python
from qiskit.quantum_info import Statevector
from numpy import sqrt
from qiskit.visualization import plot_histogram
from qiskit.quantum_info import Operator
from qiskit import QuantumCircuit

u = Statevector([1/sqrt(2), 1/sqrt(2)])
display(u.draw('latex'))
display(u.draw('text'))
display(u.is_valid())
display(u.measure())
statistics = u.sample_counts(1000)
display(statistics)
plot_histogram(statistics)


X = Operator([ [0,1],[1,0] ])
Y = Operator([ [0,-1.j],[1.j,0] ])
u = u.evolve(X)
u = u.evolve(Y)

circuit = QuantumCircuit(1)
circuit.h(0)
circuit.t(0)
display(circuit.draw())

ket0 = Statevector([1,0])
v = ket0.evolve(circuit)
v.draw('latex')

statistics = v.sample_counts(4000)
plot_histogram(statistics)
```