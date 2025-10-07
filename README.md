# Archive of ACCESS-ESM1.6 development experiments

The purpose of this repository is to archive and document payu experiments run during development of ACCESS-ESM1.6. These will include records of the the configurations, executables, input files, parameter values, and run histories from these experiments.

Each branch in this repository will correspond to a separate experiment.

### Branch name conventions
Branches in this repository use the following naming convention:
```
<GH-user-name>-<dev/test>-<YYYYMMDD>-<number>
```
where:
- `<GH-user-name>` is the GitHub user name of the person running the experiment
- `<dev/test>` is the type of experiment, where:
    - `dev` refers to experiments which are anticipated to make their way into the final model, e.g. spin-up simulations
    - `test` refers experiments used for testing different features or model changes, e.g. a parameter perturbation experiment
- `<YYYYMMDD>` is the date that the experiment started running.
- `<number>` is used to distinguish experiments run on the same date.

For example, `MartinDix-test-20250305-3` would refer to the third "test" experiment run by Martin on 2025/03/05.

### Pushing an experiment to this repository
To complete the following you need write access to this repository. To get write access, you need to [create an issue](
https://github.com/ACCESS-Community-Hub/access-esm1.6-dev-experiments/issues/new?template=repository-access-request.md) and request access.

The steps below can be followed to push an experiment to this repository. Note that github ssh keys will need to have previously been set up
1. Navigate to the experiment's payu control directory
2. Add the experiment archive repository as a second remote:
    ```
    git remote add esm1p6_dev_archive git@github.com:ACCESS-Community-Hub/access-esm1.6-dev-experiments
    ```
3. Check the branch name used in the local repository:
   ```
   git branch 
   > * <current-branch-name>
   > other-branch-1
   > other-branch-2
   ```
4. Push the experiment to this archive, assigning a branch name that matching the conventions:
    ```
    git push esm1p6_dev_archive <current-branch-name>:<user-name>-<dev/test>-<YYYYMMDD>-<number>
    ```

### Updating an archived experiment
If an experiment is updated (e.g if it's run for more time) after it has been pushed to this repository, the updates can be added to this repository with the following steps:
1. Check which branch name was previously used when pushing to `esm1p6_dev_archive`
    ```
    git branch -a
    > * <current-branch-name>
    > remotes/esm1p6_dev_archive/<remote-branch-name>
    ```
2. Push to the previously used remote branch:
    ```
    git push esm1p6_dev_archive <current-branch-name>:<remote-branch-name>
    ```

### Describing experiments
The branch naming conventions are set up to organise the archive and prevent naming clashes, however they don't contain descriptive information on the experiments. It's recomended to add a github issues to provide a brief description of each archived experiment, including:
- The branch name used
- The purpose of the experiment
- Main changes to the configuration
It's recommended to give the issue a short descriptive name, as these may be useful for finding archived experiments.
