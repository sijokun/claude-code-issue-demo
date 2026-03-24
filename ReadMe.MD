Run `claude` and ask him/her to edit test file. He is going to ask for edit when Edit is in permissions.allow

When editing files that contain a colon (:) in the file path, Claude Code prompts for permission even though Edit is in the allow list without any scope restrictions.

This affects Vue.js file-based routing projects that use :param convention for dynamic routes (e.g., src/pages/lesson/:id.vue).

## Steps to reproduce:

1. Add "Edit" to permissions.allow in .claude/settings.local.json
2. Try to edit a file with : in the path, e.g. :file.txt
3. Claude Code prompts for permission despite Edit being allowed

## Expected behavior:

Edit in the allow list without a scope should allow editing all files, regardless of characters in the path.

## Actual behavior:

The permission matcher appears to interpret the : in the file path as a scope delimiter (like Bash(git commit:*)), causing the unscoped Edit rule to not match.

