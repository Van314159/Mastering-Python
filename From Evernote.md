# Case collection

All the codes are run in jupyter notebook.

## Plot3D

### plot 3d vector.

The following code is an example of plotting 'discrete' vectors, not 'grid' 3d vectors.
```
from mpl_toolkits.mplot3d import axes3d
import matplotlib.pyplot as plt
import numpy as np
%matplotlib inline

position_velocity = np.array([np.random.sample((3,)) for i in range(10)])
x, y, z, u, v, w = zip(*whole)

fig = plt.figure(figsize=(12, 12))
ax = fig.gca(projection='3d')
ax.quiver(x, y, z, u, v, w, length=1e-2, normalize=True)
```

