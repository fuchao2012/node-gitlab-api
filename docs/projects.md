# Projects API

* [Projects](#projects)
	* [List all projects](#list-all-projects)
	* [Get a single project](#get-a-single-project)
	* [Create a project](#create-a-project)
	* [Create a project for user](#create-a-project-for-user)
	* [Edit a project](#edit-a-project)
	* [Fork a project](#fork-a-project)
	* [Star a project](#star-a-project)
	* [Unstar a project](#unstar-a-project)
* [Project Members](https://github.com/jdalrymple/node-gitlab-api/blob/master/docs/project-members.md)
* [Project Triggers](https://github.com/jdalrymple/node-gitlab-api/blob/master/docs/project-triggers.md)
* [Project Hooks](https://github.com/jdalrymple/node-gitlab-api/blob/master/docs/project-hooks.md)

## Projects

### List all projects

Get a list of visible projects for authenticated user. When accessed without authentication, only public projects are returned.

```javascript
let projects = GitlabAPI.projects.all();
```

**Parameters**: [List all projects](https://github.com/gitlabhq/gitlabhq/blob/master/doc/api/projects.md#list-projects)

**Extra Parameters**

| Argument      | Description              | Type     | Required | Default           |
|---------------|--------------------------|----------|----------|-------------------|
| max_pages     |Limits the amount of pages returned | Number   | No       |  All pages         |


### Get a single project

Get a specific project. This endpoint can be accessed without authentication if
the project is publicly accessible.

```javascript
// From a project ID
let projectA = GitlabAPI.projects.show(21);

// From a projects url
let projectB = GitlabAPI.projects.show('diaspora/diaspora');
```

**Parameters**: [Get a single project](https://github.com/gitlabhq/gitlabhq/blob/master/doc/api/projects.md#get-single-project)


### Create a project

Creates a new project owned by the authenticated user.

```javascript
let projectA = GitlabAPI.projects.create({
  // params
});
```
**Parameters**: [Create a project](https://github.com/gitlabhq/gitlabhq/blob/master/doc/api/projects.md#create-project)


### Create a project for user

Creates a new project owned by the specified user. Available only for admins.

```javascript
let projectA = GitlabAPI.projects.create({
	userId: 5,
  // params
});
```
**Parameters**: [Create a project for user](https://github.com/gitlabhq/gitlabhq/blob/master/doc/api/projects.md#create-project-for-user)


### Edit a project

Creates a new project owned by the specified user. Available only for admins.

```javascript
let projectA = GitlabAPI.projects.edit(projectId, {
  // params
});
```
**Parameters**: [Edit a project](https://github.com/gitlabhq/gitlabhq/blob/master/doc/api/projects.md#edit-project)


### Fork a project

Forks a project into the user namespace of the authenticated user or the one provided.

```javascript
let projectA = GitlabAPI.projects.fork(projectId, {
  // params
});
```
**Parameters**: [Fork a project](https://github.com/gitlabhq/gitlabhq/blob/master/doc/api/projects.md#fork-project)


### Star a project

Stars a given project. Returns status code `304` if the project is already starred.

```javascript
let projectA = GitlabAPI.projects.star(projectId);
```
**Parameters**: [Star a project](https://github.com/gitlabhq/gitlabhq/blob/master/doc/api/projects.md#star-a-project)


### Unstar a project

Unstars a given project. Returns status code `304` if the project is not starred.

```javascript
let projectA = GitlabAPI.projects.unstar(projectId);
```
**Parameters**: [Unstar a project](https://github.com/gitlabhq/gitlabhq/blob/master/doc/api/projects.md#unstar-a-project)


### Remove a project

Removes a project including all associated resources (issues, merge requests etc.)

```javascript
GitlabAPI.projects.remove(projectId);
```
**Parameters**: [Remove a project](https://github.com/gitlabhq/gitlabhq/blob/master/doc/api/projects.md#remove-project)
