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

# PART 1: Building movies list
1. Create new `Movie` class.
```
ng generate class movie
```

The `Movie` needs `title` and `poster` properties of appropriate types. Make sure to add them to the newly created class.

1. Create new `MovieService` for fetching the movies.

```
ng generate service movies
```

Copy the mocked movies data from [movies.js](movies.js).
Implement two methods in the service - `getAll(): Observable<Movie[]>` and `getByIndex(index: number): Observable<Movie`. 

1. Create new `MoviesListComponent` component to display the information for all movies.

```
ng generate component movies-list
```

Inject the `MovieService`.
Fetch all movies and display them in the templates for web and mobile.
> Notice that both service methods return `Observable`! You may need to use the [`async` pipe](https://angular.io/api/common/AsyncPipe).

1. Display the `MoviesListComponent`.

Provide the `MoviesListComponent` as a route in `src/app/app.routes.ts`.
Make the default `/` route redirect to the movies list route.
> Hint: You have to change the first route in the `routes` array.

# PART 2: Building movie details

1. Create new `MovieDetails` component
```
ng generate component movie-details
```

1. Register as a route.

Register the `MovieDetails` component as a route in `src/app/app.routes.ts`.
Provide the index of the movie in the array as param.

1. Navigate to `MovieDetails`.

Go to the `MoviesListComponent` template.
Add a button that navigates to the `MovieDetails` page on click/tap.
> You should use the \<router-link\> and \<ns-router-link\> directives.

1. Fetch the movie

Go to the `MovieDetailsComponent` TS file again.
Resolve the movie index from the `ActivatedRoute`. Fetch the movie from the `MovieService`.

1. Display the movie

Go to the template of the `MovieDetailsComponent`.
You have the movie in your component class - now display it on the screen. Get creative!
