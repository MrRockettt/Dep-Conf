# Dep-Conf
RCE via Dependency Confusion Attack javascript

## One-liner
find . -type f -name package.json | xargs -n1 -I{} cat {} | jq -r '.dependencies + .devDependencies' | cut -d : -f 1 | tr -d '"|}|{' | sort -u | tr -s "     " | sort -u | xargs -n1 -I{} echo "https://registry.npmjs.org/{}" | grep -v "@" | httpx -status-code -silent -content-length -mc 404

## Tools
https://github.com/tomnomnom/fff
https://github.com/gabrie30/ghorg

https://github.com/tomnomnom/dotfiles/blob/master/scripts/git-dump
