docker run -it --rm -v $(pwd):/src -p 1313:1313 --entrypoint=/bin/bash peaceiris/hugo:v0.125.4

curl -L https://go.dev/dl/go1.22.5.linux-amd64.tar.gz -o go1.22.5.linux-amd64.tar.gz &&\
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.22.5.linux-amd64.tar.gz &&\
export PATH=$PATH:/usr/local/go/bin

hugo mod init mn
hugo server -D --bind 0.0.0.0


git checkout main
git cherry-pick ${LAST_COMMIT_IN_CONFIG_BRANCH}
cp -r public/* .
