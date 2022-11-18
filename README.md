# uav

A long-range autonomous UAV for spotfire detection.

## Project structure

TODO


## Git Hygiene guide

For this project we will be using standard software engineering principles for our version control.

### Branches and forks

The most important of these is to **make sure to make a fresh pull request for every new feature**. If you want to work on the main repo, this also means a new branch for every feature. If you are using forks, you can branch as you please.

In this case a "feature" is any atomic piece of work you might be contributing, i.e. small enough that you are the only one likely to be working on it. For example, if you are working in /hardware you might implement the module to translate celestial coordinates to motor positions as a feature.

In the case that you are working on a bigger part with another person (or people) you can make a branch with sub-branches for each feature.

### Code review and pull requests

**Never commit directly to main**. The only exception to this is for making administrative changes like editing the readme, .gitignore, .codeowners and so on.
Whenever you finish a feature on a branch like described above, you should submit a **pull request** to get it merged back into a parent branch. Pull requests are also known as "merge requests" on GitLab and some other services (far clearer name frankly) because they basically give you a chance to write up what you've done and documents all the changes you are going to make. It also lets you safely specify how you are going to handle any conflicts between your branch and the parent.

Once you have made your pull request you should ideally get somebody else who didn't contribute to do a **code review** for you. This is mostly important on larger features or things where a lot can go wrong. While this project doesn't have critical stakes or a deployment to risk, it's a very important habit and will often catch a lot of mistakes that are very hard to find on your own (especially when they are errors in design rather than in code).

## Programming style and toolchain

### Python

For Python we will be using PyLint for keeping things neat and following the Python Foundation styleguide (automatically enforced by PyLint). You can install it with ``pip install pylint``. You should also make sure you install the Python language pack for VSCode. If you use a different IDE just Google "python [language]".
VS Marketplace Link: <https://marketplace.visualstudio.com/items?itemName=ms-python.python>

### C / C++ / Rust

For C-based languages we will use the Google Style guide <https://google.github.io/styleguide/cppguide.html>. For Rust we will use the Mozilla style guide <https://github.com/rust-dev-tools/fmt-rfcs>. Below is a list of quirks we need to be aware of for the platforms involved.

#### Raspberry Pi

For C and C++ we will be using GCC and the rest of the GNU C toolchain because it is by far the easiest to use.

#### Microcontrollers

For all of our microcontrollers (Arduino or otherwise) we will try and use C++ where possible. Bear in mind that you usually can't use the standard library which effectively transforms C++ into C with classes. Rust is more efficient but embedded support is not nearly as sophisticated just yet - it is *significantly* faster and more expressive than C/C++ however so it is superior.

#### PC / Mac / Linux

Since the target platform is the Raspberry Pi (on Raspbian), all development work should ideally be done on a UNIX-based platform - WSL2 if you are on Windows. If you use macOS, you can just proceed as normal; although correct operation is not guaranteed.
