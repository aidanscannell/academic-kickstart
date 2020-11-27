# Aidan Scannell's Academic Kickstart

1. Create a new blog post using org-capture SPC+o+c h.
1. Create a new project/publication/talk,
   ```
   hugo new --kind project project/<NAME-OF-POST>
   ```
2. Export org sub-tree (a single blog post) to markdown in /posts/../ folder using C-c C-c H H
3. To serve the site locally run,
    ```
    hugo server --disableFastRender
    ```
    or to include drafts use,
    ```
    hugo server --disableFastRender -D
    ```
    or use spacemacs SPC+p+c.

4. Pushing to GitHub will auto deploy on netlify.
