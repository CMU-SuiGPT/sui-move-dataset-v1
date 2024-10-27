```
git clone --recurse-submodules -j8 git@github.com:CMU-SuiGPT/sui-move-dataset-v1.git
cd sui-move-dataset-v1
for dir in ./move_repos/*; do (cd "$dir" && git checkout $(git branch --show-current)); done
```
