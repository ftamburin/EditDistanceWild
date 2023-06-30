# EditDistanceWild
Edit Distance with Wildcards for CPU and CUDA both simple and normalised by using the Generalised Edit Distance [(Li, Liu 2007)](https://ieeexplore.ieee.org/document/4160958). It requires pytorch.

It allows for two wildcards: '?' means any single symbol and '*' means any sequence of symbols. 

## For building and testing:
```
    git clone https://github.com/ftamburin/EditDistanceWild
    cd EditDistanceWild
    python3 setup.py install
    python3 test/example.py
```
If a GPU is present, it builds both versions for CPU and GPU.

## API
Two functions are exposed (look at example.py):
- **editdistance(x,y,pad,wID,wS)** that compares two padded pytorch tensors (**x** and **y**) elementwise.
- **editdistance1N(x,y,pad,wID,wS)** that compares a single word (as a pytorch tensor **x**) with all the elements of a padded pytorch tensor (**y**).
**pad** represents the value used for padding
**wID** and **wS*** are respectively the weigth for insertions/deletions and substitutions.

Both functions return a pytorch tensor [:,2]: the first column contains the simple Edit Distance with Wildcards and the second the corresponding normalised version. 

Examine the file test.py in the example folder for any clarification.

Tested on:
- CUDA 11.4
- python 3.7
- pytorch 1.10.2

Parts of this package are based on [an early and buggy version from Francesco Castelli](https://github.com/francescocastelli/torchdistance).

If you find this code useful in your research, please cite:
```
@InProceedings{Tamburini:2023:ACL-CAWL,
  author    = {Tamburini, Fabio},
  title     = {Decipherment of Lost Ancient Scripts as Combinatorial Optimisation using Coupled Simulated Annealing},
  booktitle = {Proceedings of the 1st ACL Workshop on Computation and Written Language (CAWL)},
  month     = {July},
  year      = {2023},
  address   = {Toronto, Canada},
  publisher = {Association for Computational Linguistics}
}
```

In case of problems contact me at <fabio.tamburini@unibo.it>.
