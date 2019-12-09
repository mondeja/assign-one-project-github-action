# GitHub Action for Assing to One Project

[![Docker Automated build](https://img.shields.io/docker/automated/srggrs/assign-one-project-github-action)][docker]
[![Docker Build Status](https://img.shields.io/docker/build/srggrs/assign-one-project-github-action)][docker]
[![Docker Pulls](https://img.shields.io/docker/pulls/srggrs/assign-one-project-github-action)][docker]
[![Docker Stars](https://img.shields.io/docker/stars/srggrs/assign-one-project-github-action)][docker]
[![GitHub](https://img.shields.io/github/license/srggrs/assign-one-project-github-action)](https://github.com/srggrs/assign-one-project-github-action/blob/master/LICENSE)

[docker]: https://hub.docker.com/r/srggrs/assign-one-project-github-action

Automatically add an issue or pull request to specific [GitHub Project](https://help.github.com/articles/about-project-boards/) when you __create__ them. By default the issues are assinged to the `To do` column and the pull requests to the `In progress` one, so make sure you have those columns in your project dashboard.

## Ackowlegment & Motivations

This action has been modified from the original action from [masutaka](https://github.com/masutaka/github-actions-all-in-one-project). I needed to fix it as the original docker container would not build. Also I think the GitHub Action syntax changed a bit.

## Inputs

### `project`

**Required** The url of the project to be assigned to.

### `GITHUB_TOKEN`

**Required** The enviromental variable for query github API.

## Example usage

Example of action:

```yaml
name: Auto Assign Project

on: [pull_request, issues]
env:
  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

jobs:
  assign_one_project:
    runs-on: ubuntu-latest
    name: Assign to One Project
    steps:
    - name: Run assignment to one project
      uses: docker://srggrs/assign-one-project-github-action:1.3.0
      if: github.event.action == 'opened'
      with:
        project: 'https://github.com/srggrs/assign-one-project-github-action/projects/2'
```
