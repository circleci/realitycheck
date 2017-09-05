# realitycheck
A sample app that reality checks some things:
1. Runs all known resource_class options
2. Runs a machine executor & remote docker 
3. Read/write workspaces
4. Tests that the org-global context is working (*NOTE:* needs a key called `CONTEXT_END_TO_END_TEST_VAR` to exist in the `org-global` context)
