```
git clone --recurse-submodules -j8 git@github.com:CMU-SuiGPT/sui-move-dataset-v1.git
# Go into the folder then init the sub-modules
cd sui-move-dataset-v1
for dir in ./move_repos/*; do (cd "$dir" && git checkout $(git branch --show-current)); done
```
