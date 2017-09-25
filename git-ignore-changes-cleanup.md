1. Modify `.gitignore`, commit, push.
2. `git rm --cached dir/dir/ -r` will recursively remove all cached files within dir/dir. Files will still be in the dir/dir/, but git will "think" files from dir/dir/ are gone. **Omitting `--cached` will remove actual files** + git will "think" files from dir/dir/ are gone.
3. `git add dir/dir/.gitignore -f` if internal .gitignore file exists, `-f` will force the file to be added, because one line above we told to remove everything so git "thinks" no files are in dir/dir/
4. `git commit -m 'Git cache cleanup'`
5. `git push origin master`
