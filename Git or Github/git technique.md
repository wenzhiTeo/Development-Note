### Revert changes but remain existing commit for references

Retrieve the latest file from base branch 
`git checkout main -- path/to/file`

Just add the file you trying to recover/revert and do commit


### Move file location
`git mv <source> <destination>`

**Example:** `git mv src/components/xxx/aaa.js src/components/aaa.js`
