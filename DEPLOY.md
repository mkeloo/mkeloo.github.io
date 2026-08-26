# Deploying to mkeloo.github.io

The `gh` CLI on this machine is signed in as `mokshIW`, not `mkeloo`.
Add and switch to the personal account first, then push.

## 1. Authenticate as mkeloo

    gh auth login          # choose GitHub.com, HTTPS, log in with a browser as mkeloo
    gh auth switch --user mkeloo
    gh auth status         # confirm the active account is mkeloo

## 2. Create the repo and push

    cd /Users/mokshkeloo/DokployProjects/JobSearch/site
    gh repo create mkeloo.github.io --public --source=. --remote=origin --push

## 3. Turn on Pages

    gh api -X POST repos/mkeloo/mkeloo.github.io/pages \
      -f 'source[branch]=main' -f 'source[path]=/'

The site appears at https://mkeloo.github.io/ within a few minutes.

## Updating later

Rebuild `index.html` from `../resume-onepage.html` (drop the phone number and add
the print button), then:

    git add index.html
    git commit -m "Update resume"
    git push
