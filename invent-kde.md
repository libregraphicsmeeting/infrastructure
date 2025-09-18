# Using the KDE infrastructure

- Our contact person at KDE is Ben Cooksley (ale is in touch with him)
- The DNS ownership and management has been moved to the KDE project
- We are testing

## Testing the Gitlab platform on KDE

- The online IDE does not seem to work correctly
- The main branch shall be named `master` and not `main` (`main` gets refused on push)
- Trying to get the CI to publish static files:
  - I've created https://invent.kde.org/aleri/htdocs-test/
  - We were given https://websites.local-kde.org/-/kde-org/-/jobs/3370175/artifacts/public/index.html as an example of deployed site
  - This is the `gitlab-ci.yml` file for the kde.org site: https://invent.kde.org/websites/kde-org/-/blob/master/.gitlab-ci.yml
  - A _standard_ `gitlab-ci.yml` file failed to run:
    - https://invent.kde.org/aleri/htdocs-test/-/commit/11ab1d2f7deab02616bf6500d25aeb68012af603
    - https://invent.kde.org/aleri/htdocs-test/-/pipelines/1042388

## User accounts on invent.kde.org

- go to https://invent.kde.org
- klick on "Sign in" in the top right corner
- Follow the link to register and do so on he KDE Identity site
- Sign In in the invent.kde.org site

TODO:

- How to join the LGM group on invent.kde (the group does not exist yet)
