This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

# Using this project

Clone the repo and `npm install`

# Husky Setup - From Scratch

### Step 1: Install `husky` as a dev dependency

```
npm install husky --save-dev
```

### Step 2: Enable Git Hooks

```
npx husky install
```

### Step 3: Add `prepare` script to `package.json` to enable Git hooks on `npm install`

```
npm pkg set scripts.prepare="husky install"
```

OR

```
npm set-script prepare "husky install"
```

### Step 4: Add a hook

```
npx husky add .husky/pre-commit "npm test"
```

This generates the .husky/pre-commit file which can be pushed (to share husky config)

### Step 5: Make a commit.

The added hooks will run before the commit, and failure will prevent the commit.

# Setting up branch name validation

### Step 1: Install `validate-branch-name` as a dev dependency

```
npm install validate-branch-name --save-dev
```

### Step 2: Add config for `validate-branch-name` in `package.json`

```
// package.json

"validate-branch-name": {
		"pattern": "^(main|develop){1}$|^(feature|hotfix)/[a-z0-9-_]+$",
		"errorMsg": "Invalid branch name. \n 1.Branch names can contain lowercase characters, numbers, hyphen and underscore. \n 2.Except for 'main' and 'develop', branch names must begin with 'feature/' or 'hotfix/' "
	},
```

### Step 3: Update .husky/pre-commit with a new hook

```
npx husky add .husky/pre-commit "npx validate-branch-name"
```
