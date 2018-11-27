# Setup

You need a few globally installed node packages.
1. `nativescript` - the NativeScript CLI knows how to build, install and run NativeScript projects.
2. `@nativescript/schematics` - schematics collections that helps with manipulating, scaffolding and organizing NativeScript projects with the Angular CLI.
3. `@angular/cli` - the Angular CLI knows how to build Angular projects for the web and execute commands from our schematics collection.

```
npm install -g nativescript @nativescript/schematics @angular/cli
```

# Create new project

You can use the Angular CLI to create the new project. The `@nativescript/schematics` collection contains our code-sharing template.

```
ng new --collection=@nativescript/schematics star-wars --shared
```

# Run the apps

For running the web application you can use the Angular CLI again:

```
ng serve --open 
```

For running the NativeScript application you should use the NativeScript CLI.
> Important: Always provide the `--bundle` flag when running the mobile application!

If you have native setup (Java, Android SDK for Android or xCode for iOS), you can use the `run` command:

```
tns run --bundle
```

If you didn't bother with setting up your machine, you should use the `preview` command:

```
tns preview --bundle
```

# Building movies list
1. Create a `Movie` class.
```
ng generate class movie
```

The class should have `title` and `poster` properties of appropriate types.

1. Create a new `MovieService` for fetching the movies.

```
ng generate service movies
```

Copy the mocked movies data from [movies.js](movies.js).
Implement two methods in the service - `getAll(): Observable<Movie[]>` and `getById(id: number): Observable<Movie`. 

1. Create a new component for the movies list.

```
ng generate component movies-list
```
Inject the `MovieService`.
Get all movies and display them in the templates for web and mobile.

