[https://youtu.be/5YZz38U20ws](https://youtu.be/5YZz38U20ws)

1. Create a repository or [fork the md repo](https://linked-blog-starter.vercel.app/publish-your-obsidian-notes-with-linked-blog-starter) in github
2. [Download Git](https://git-scm.com/downloads)
3. Create a [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-personal-access-token-classic) from github![create-pat-github.png](https://linked-blog-starter.vercel.app/md_assets/attachments/create-pat-github.png)
4. Install the [Obsidian Git](https://github.com/denolehov/obsidian-git/wiki/Installation) community plugin
5. Create a folder to store the repository. (e.g. `remote-blog/`). Set scopes to repo & expiration to no expiration
6. Run the command (CMD/Ctrl + P): `Clone an existing remote repo`![clone-repo-git-plugin.png](https://linked-blog-starter.vercel.app/md_assets/attachments/clone-repo-git-plugin.png)
7. Paste the URL of the forked repository in the following format

```
https://<PERSONAL_ACCESS_TOKEN>@github.com/<USERNAME>/<REPO>.git
```

For example it might look like this:

```
https://ghp_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX@github.com/ithinkwong/linked-blog-starter-md.git
```

7. Then type in the folder you created in step 5 (e.g. `remote-blog/`)
8. Restart Obsidian
9. Make edits to your notes
10. Publish your notes run the command "Obsidian Git: Create backup" by opening the command palette (CMD/Ctrl + P)