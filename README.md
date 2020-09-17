# JS Package Info
GitHub Action to analyze the packages used in a JavaScript project. Helps maintainers have control over the packages used in the project.

What it does:
 - Lists the unused packages
 - Lists the expected size of the node modules after deployment

## Usage
Adding the following to your workflow will create a new job using the js-package-info Actions.
  
```on: [pull_request]

jobs:
  js-package-info:
    runs-on: ubuntu-latest
    name: An Action to analyze javascript packages
    steps:
    - uses: actions/checkout@v2
    - uses: actions/setup-node@v1
      with:
        node-version: '12'
    - run: npm install -g bundle-phobia-cli
    - run: npm install -g depcheck
    - name: Get Package Info
      uses: DesignrKnight/js-package-info@v2
      with:
        node_dir: './'
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

## Inputs
#### node_dir

The default is ```./```. Change it to point to the relative location of the package.json file in the git repo. If the location is ```./server/package.json```, then the environment variable will be ```./server/```

#### GITHUB_TOKEN

The GitHub token from context is used to run this Actions. Leaving this unchanged should work for almost all use cases.

## Troubleshooting
Suggestions and issues can be posted on the repository's 
[issues page](https://github.com/DesignrKnight/js-package-info).


## Dependencies
The Actions uses the following for its working.
 - [actions/checkout@v2](https://github.com/actions/checkout)
 - [actions/setup-node@v1](https://github.com/actions/setup-node)
 - [bundle-phobia-cli](https://www.npmjs.com/package/bundle-phobia-cli)
 - [depcheck](https://www.npmjs.com/package/depcheck)


## License
See the [License File](https://github.com/DesignrKnight/js-package-info/LICENSE).
