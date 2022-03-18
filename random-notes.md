  #### How to determine your PROJECT at various machines

  - `gsissh stampede2 /usr/local/etc/taccinfo`
  - `gsissh expanse 'module load sdsc; expanse-client user'`

  #### Installing HPC Annex on OSG Connect (for the demo)

  - `git clone https://github.com/htcondor/htcondor.git`
  - (check out the appropriate branch)
  - install token in `~/.condor/tokens.d`
    ```
    condor_token_create -identity tlmiller@annex.osgdev.chtc.io \
         -authz READ \
         -authz ADVERTISE_STARTD \
         -authz ADVERTISE_MASTER \
         -authz ADVERTISE_SCHEDD \
     > tlmiller@annex.osgdev.chtc.io```
  - mkdir `~/.hpc-annex`  (should this become `~/.condor/hpc-annex`?)
  - set `LIBEXEC` in `~/.condor/user_config` because the system install
    of HTCondor doesn't have HPC Annex yet, to `~/condor/install/libexec`,
    which contains an `annex` symlink pointing at `src/condor_scripts/annex`.
  - `src/condor_tools/htcondor` invokes properly...