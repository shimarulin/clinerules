## Brief overview
This set of guidelines establishes rules for cloning repositories specifically for studying code as examples, ensuring organized storage and avoiding naming conflicts.

## Repository cloning workflow
- MUST use the `.references/` directory for cloning repositories intended for code study purposes
- MUST create the `.references/` directory if it does not exist before cloning
- MUST rename the cloned repository directory to include the username (typically the part before the repository name in the URL) to prevent conflicts when repositories from different users have identical names
- SHOULD check existing repositories in `.references/` directory and continue sequential numbering from the next available number
- SHOULD use batch cloning commands with `for repo in` for multiple repositories to optimize the process
- MUST handle repositories with specific branches using `--branch <branch-name>` in git clone command
- SHOULD name repositories with sequential numbering in the range 000-999 based on cloning order for better organization
- Example: For a repository at `https://gitlab.com/smonoscr/nixfiles`, clone and rename the directory to `001_smonoscr_nixfiles` within `.references/` (where 001 is the sequential number)
- Example: For batch cloning with numbering: `cd .references; next_num=$(ls -d [0-9][0-9][0-9]_* 2>/dev/null | sort | tail -1 | cut -d'_' -f1 | awk '{print $1+1}' | xargs printf "%03d"); for repo in repo1 repo2; do user=$(echo $repo | cut -d'/' -f1); name=$(echo $repo | cut -d'/' -f2); git clone https://github.com/$repo && mv $name ${next_num}_${user}_$name; ((next_num++)); done`
- Example: For specific branch: `git clone --branch branch-name https://github.com/user/repo && mv repo 002_user_repo` (with sequential numbering)
