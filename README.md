## For searx instance operators

* [Create an issue](https://github.com/dalf/searx-instances/issues/new/choose) to add / remove / edit a searx instance on https://searx.space/
* If you add a new instance: allow the IPs 2001:41d0:8:de3::1 and 176.31.252.227 to access your instance. https://searx.space/ will check your instance periodically ([source code](https://github.com/dalf/searx-stats2)) 
* Way for a reviewer to actually change [searxstats/instances.yml](https://github.com/dalf/searx-instances/blob/master/searxinstances/instances.yml)

## For reviewers

* on each commit, instances.yml is checked
* ```python -m searxinstances.update``` allows to edit the instances.yml

```
usage: update.py [-h]
                 [--github-issues [GITHUB_ISSUE_LIST [GITHUB_ISSUE_LIST ...]]]
                 [--add [ADD_INSTANCES [ADD_INSTANCES ...]]]
                 [--delete [DELETE_INSTANCES [DELETE_INSTANCES ...]]]
                 [--edit [EDIT_INSTANCES [EDIT_INSTANCES ...]]]

Update the instance list according to the github issues.

optional arguments:
  -h, --help            show this help message and exit
  --github-issues [GITHUB_ISSUE_LIST [GITHUB_ISSUE_LIST ...]]
                        Github issue number to process, by default all
  --add [ADD_INSTANCES [ADD_INSTANCES ...]]
                        Add instance(s)
  --delete [DELETE_INSTANCES [DELETE_INSTANCES ...]]
                        Delete instance(s)
  --edit [EDIT_INSTANCES [EDIT_INSTANCES ...]]
                        Edit instance(s)
```

The tool :
* is only an helper. instances.yml can be edited directly.
* shows the default editor to only edit one instance at a time.
* once the user quits the editor, the script checks everything is okay, if not it goes back to the editor with the error added at the end of the buffer.
* if everything is okay, the script modifies the instances.yml file.
* then it creates a commit.
* The ```--github-issues``` options reads the [github issues](https://github.com/dalf/searx-instances/issues).

---

An example what is shown in the default editor:
```
https://nibblehole.com: {}

# Add https://nibblehole.com
#
# Close https://github.com/dalf/searx-instances/issues/2
# From @dalf

#> The above text is the commit message
#> Delete the whole buffer to cancel the request

#> -- MESSAGE -----------------------
#> See https://github.com/asciimoo/searx/pull/1818
```

Here is it possible to modify the yaml, the commit message and validate or delete the whole buffer to cancel.
