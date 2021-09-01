# Endpoint Versioning

- `git push -u origin new-branch`
- Make a `pull request` from `new-branch` to `master`
    - Add a reviewer
- After being approved update local repository: 
    - `git checkout master`
    - `git branch -d new-branch`
    - `git pull`
- Add tag and push changes
    - `git tag -a v1.0.0 -m "A message"`
    - `git push origin --tags`
- Update version on Account Manager
    - Go to `Account Manager > Endpoints > EndpointName`
    - Use `Tools > Manage versions`
    - Refresh versions
    - Select version actions and use Build version
- Then deploy endpoint on monitor or remove and add endpoint in builder

