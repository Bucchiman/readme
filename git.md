<!--
 FileName:      git
 Author:        8ucchiman
 CreatedDate:   2023-06-18 00:52:15
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     https://zenn.dev/hankei6km/articles/git-rebase-onto
                https://gist.github.com/hankei6km/4301ebc7e320b987de1f7a5b0acb994a
 Description:   ---
-->



<!--
--   Keywords     : branching, name
--   Reference: https://dev.to/couchcamote/git-branching-name-convention-cch
-->

# Branch naming convention
## Code flow branches
### Development (dev)
- All new features and bug fixes should be brought to this branch.
- Resolving developer codes conflicts should be done as early as here.

### QA/Test (test)
Contains all codes ready for QA testing

### Staging (staging, Optional)


### Master (master)

## Temporary branches
### Feature
The branch is created based on the current development branch.
When all changes are Done, a Pull Request is needed to put all of these to the development branch.

- Examples
    - feature/integrate-swagger
    - feature/JIRA-1234
    - feature/JIRA-1234_support-dark-theme

It is recommended to use all lower caps letters and hyphen to separate words.

### Bug Fix

### Hot Fix
### Experimental
### Build
### Release
### Merging
