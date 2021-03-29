# duplicate-bib-fix
Small python script to check and replace duplicated bib entries in your tex files

## What this does?
This reads your bibliographic entries and makes a python dictionary of duplicated entries. It then reads your `*.tex` files and replaces all those duplicated entries with one common entry. For eg:
```
...
'vihinen1994accuracy': ['Vihinen1994-sd', 'Vihinen1994-vq']
...
```
Here `vihinen1994accuracy, Vihinen1994-sd, Vihinen1994-vq` all refer to the same entry. This script reads your *.bib file and finds out such duplicates. Then it reads your chapter and replaces every instance of `Vihinen1994-sd, Vihinen1994-vq` with `vihinen1994accuracy`. Yor citations will then have no more duplicates!

Any changes made to your original chapter will be saved as a new file named `_replaced_.tex`. This will fix 95% of your problems (it certainly fixed mine!). However, you might still need to manually go through your references. For example, entries with title such as `Multiple roles of the coding sequence 5' end...` and `Multiple roles of the coding sequence 5^{\prime} end...` are the same but we cannot yet merge as one entry. Currently, we use `\\emph` and `\textit` as single entry because this is only so much that I can do.


### How to
See ```duplicate-bib-fix.ipynb``` for details. This is a Jupyter notebook file so you need to have Jupyter installed.


### Notes:
#### bib entries should be separated by space in your .bib file. For eg: 
```
@article{breiman2001random,
  title={Random forests},
  author={Breiman, Leo},
  journal={Machine learning},
  volume={45},
  number={1},
  pages={5--32},
  year={2001},
  publisher={Springer}
}

@book{james2013introductiontostatlearning,
  title={An introduction to statistical learning},
  author={James, Gareth and Witten, Daniela and Hastie, Trevor and Tibshirani, Robert},
  volume={112},
  year={2013},
  publisher={Springer}
}

```

Example .bib file and a chapter from my own thesis are included. 
