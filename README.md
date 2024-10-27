```
git clone --recurse-submodules -j8 git@github.com:CMU-SuiGPT/sui-move-dataset-v1.git
# Go into the folder then init the sub-modules
cd sui-move-dataset-v1
echo "Initializing submodules and checking out the current branch for each submodule..."

# Calculate the total number of submodule directories
total_dirs=$(find ./move_repos/* -type d | wc -l)
count=0

for dir in ./move_repos/*; do
    # Enter each submodule directory and check out the current branch, hiding output
    (cd "$dir" && git checkout $(git branch --show-current) > /dev/null 2>&1)
    count=$((count + 1))
    
    # Calculate and display progress bar
    progress=$((count * 100 / total_dirs))
    echo -ne "Progress: ["
    for ((i=0; i<progress/2; i++)); do echo -n "#"; done  # Filled part of the bar
    for ((i=progress/2; i<50; i++)); do echo -n " "; done  # Empty part of the bar
    echo -ne "] $progress% ($count/$total_dirs)\r"         # Display percentage and count
done

# New line after completion
echo -e "\nAll submodules have been initialized and checked out."
```
