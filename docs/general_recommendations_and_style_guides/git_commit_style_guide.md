---
title: Git commit style guide
parent: General recommendations and style guides
nav_order: 1
---

# Git commmit style guide
{: .no_toc }

## Table Of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Line size

You should limit your **subject line size** to *50 characters* or **maximum 72**. It is not a hard limit, just an approximate number. Keeping subject lines at this length ensures that they are readable, and forces the author to think for a moment about the most concise way to explain what’s going on. The body should be wrapped at about **72 characters**.

A commit with a long subject line wraps and elipses if it's too long:

<img src="../../../assets/images/bad_commit_message_example1.png" >

If you hover on it, you will see how it was written in one line:

<img src="../../../assets/images/bad_commit_message_example1_1.png" >

In `git log` it's also just a one line:

<img src="../../../assets/images/bad_commit_message_example1_2.png" >

And compare it, to a good written commit:

<img src="../../../assets/images/good_commit_message_example1.png" >

Much more easy to read right?

### How to measure line size?

<!-- TODO: Learn about git hooks -->
You can ether use an **editor**, or **git hooks**. I currently don't know how to use git hooks, I'll write about them later, but, as I know, they can automaticaly format commit messages for you if you configure them.

On the other side you can just type `git commit` and it will open editor you set with `git config core.editor <editor>` to edit the commit message, for example I use Helix and for me it looks looks like this, automatically showing 50 and 72 character marks:

<!-- TODO: Make better commit message in an editor picture -->
<img src="../../../assets/images/commit_message_in_an_editor.png" >

Your favourite editor may not show you there you should wrap the line, but I'm sure it does display current cursor position on the line, so you'll be fine.


## Conventional commits

The Conventional Commits specification is a lightweight convention on top of commit messages. It provides an easy set of rules for creating an explicit commit history; which makes it easier to write automated tools on top of.

Then writing a commit message it must be structured as follows:

<!-- Thanks again https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13 -->
> <pre>
> <b><a href="#types">&lt;type&gt;</a></b>(<b><a href="#scopes">&lt;optional scope&gt;</a></b>): <b><a href="#description">&lt;description&gt;</a></b>
> <sub>empty line as separator</sub>
> <b><a href="#body">&lt;optional body&gt;</a></b>
> <sub>empty line as separator</sub>
> <b><a href="#footer">&lt;optional footer&gt;</a></b>
> </pre>

Initial commit:
```text
chore: init
```

Merge commit:
```text
Merge branch '<branch name>'
```
<sup>Follows default git merge message</sup>

Revert commit:
```text
Revert "<reverted commit subject line>"
```
<sup>Follows default git revert message</sup>

### Types

- `feat` Commits that add, adjust or remove a feature to/of/from the API or UI
- `fix` Commits that fix an API or UI bug of a preceded `feat` commit
- `refactor` Commits that rewrite or restructure code without altering API or UI behavior
  - `perf` Commits are special type of `refactor` commits that specifically improve performance
- `docs` Commits that exclusively affect documentation
- `test` Commits that add missing tests or correct existing ones
- `cl` Commits that affec deployment scripts, CI/CD pipelines, backups, monitoring, or recovery procedures
- `chore` Commits that represent tasks like initial commit, modifying .gitignore, version change and etc.

Depending on the project and it's specific modules, there *might be more types added*, for example `db` (related to Database changes), or `build` (related to project build process), but invent new types only then it's indeed necessary, because most of the time existing type with a scope is enough to specify what exact type of change commit does.

{: .note}
> If you can't decide one type for your commit, that means you're commiting too much at once. `git add <file ...>` and `git commit` as many times as you need to keep everything pretty and clean.

### Scopes

The `scope` provides additional contextual information.

- The scope is an *optional* part
- Different repos and projects can have different scopes

Then you make a change you usally can specify the scope, for example `feat(admin)` (will be some sort of a new feature for admin), `feat(navigation)` (will be some sort of feature related to navigation), `fix(api)` (will fix some issues related to API) and etc. If you can't specify a scope then don't.

### Breaking changes indicator

This indicator signals that the changes may **disrupt existing functionality** for users or other developers, **breaks** their workflow if you want.

- A commit that introduce breaking changes must be indicated by an ! before the : in the subject line e.g. `feat(api)!: remove status endpoint`
- Breaking changes should be described in the commit footer section, if the commit description isn't sufficiently informative

For exmple change function name, return type or input parameters, remove API endpoint, dropping platform support, changing default behavior.

### Description

The description contains a concise description of the change.

- The description is **mandatory**
- Use the **imperative, present tense**: "**change**" not "changed" nor "changes". Think of `If applied, this commit will...`
- Do not capitalize the first letter
- Do not end the description with a period (.)
- In case of breaking changes also see [breaking changes indicator](#breaking-changes-indicator)

### Body

The body should include the further description of the change and motivation for the change and contrast this with previous behavior if necessary.

- The body is an optional part
- You can use bullet points (- or *) here

Sometimes you don't need to add body if description is self explanatory, for example `docs: fix typo`, or `chore(cl): update actions' versions`, or `refactor!: change 'request()' function name to 'sendRequest()'` and etc.

### Footer

The footer should contain issue references and informations about breaking changes if needed.

- The footer is an *optional* part
- Optionally reference issue identifiers (e.g., Resolves: #123, See also: #456, #789)
- Breaking Changes must start with the word BREAKING CHANGE:
- For a single line description just add a space after BREAKING CHANGE:
- For a multi line description add two new lines after BREAKING CHANGE:

## Examples

[Source](https://github.com/ziglang/zig/commit/c5383173a0de17210f3036acd942738e906997e5)
```text
compiler: replace @Type with individual type-creating builtins

The new builtins are:
* `@EnumLiteral`
* `@Int`
* `@Fn`
* `@Pointer`
* `@Tuple`
* `@Enum`
* `@Union`
* `@Struct`

Their usage is documented in the language reference.
There is no `@Array` because arrays can be created like this:

    if (sentinel) |s| [n:s]T else [n]T

There is also no `@Float`. Instead, `std.meta.Float` can serve this use
case if necessary.

There is no `@ErrorSet` and intentionally no way to achieve this.
Likewise, there is intentionally no way to reify tuples with comptime
fields, or function types with comptime parameters. These decisions
simplify the Zig language specification, and moreover make Zig code more
readable by discouraging overly complex metaprogramming.

Co-authored-by: Ali Cheraghi <alichraghi@proton.me>
Resolves: #10710
```

[Source](https://github.com/Satty-org/Satty/commit/e383c984d7474589d20cbe6898c6dc5d98742ae)
```
fix: pan with middle mouse button in zoom != 1.0 (#532)

When dragging with a zoom != 1.0 the pixel where dragging started
does not stay under the mouse pointer as the event.pos used for the
pan is in image coordinates.

Thus add a new event.screen_pos to the MouseEventMsg and keep
event.pos which is transformed to image coordinates for tool in
handle_event_mouse_input().
```

[Source](https://github.com/Satty-org/Satty/commit/fdb72cf7e16aaeb21733df45fa61d4ca5108866d)
```
chore: adjust dependabot config

This is an attempt to reduce the noise.

Closes: #280
```

## References

I heavily relied on those references and coppied a lot from them. Really recommend to check those out.

- [Conventional Commits Chetsheet](https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13)
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
- [How to Write a Git Commit Message](https://cbea.ms/git-commit/)
