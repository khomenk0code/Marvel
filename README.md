# SPA on the subject of MARVEL characters and comics.

### List of technologies involved
- React.js, react-router-dom, react-transition
- CSS modules, Styled Components, Grid CSS

### About the application
The main idea of the application is to display to the user information about the characters and logs, the data of which comes from real-time requests from a remote server.
This application is a **_single page application_**, where the UI part is developed on **_React_**. Interaction occurs with a third-party open API provided by Marvel Studios.
Information can be provided in the form of list pages, individual item pages, character search results.

### General technical details
- Interaction with the subsequent processing and display of data on the open [Mavrel API](https://developer.marvel.com/) with the databases of this film studio has been built.
- Implemented portal routing without reloads (react-router-dom)
- Implemented utilities for obtaining data, conditional rendering, depending on the type of application page.
- On the MainPage.js page, all components are wrapped in ErrorBoundary.js
- In App.js app pages are loaded lazily via React.lazy & Suspense

### The structure of the UI part.
The application is represented by pages: MainPage, ComicPage, SinglePage (for both comics and characters), 404.
#### More about MainPage.
Consists of components:
- RandomChar: every 60 seconds or on click, a random character is requested by a randomly generated ID. You can go to the character page.
- CharList: characters coming from the Marvel API are displayed in portions of 9 elements. There is Pagination - loading characters on click. By clicking on any character, information about him will be displayed in the sidebar. The React Transition library is used to animate the cards.
For a chunked data request, the UseGetAllCharactersQuery hook from apiChar is used. Hook at each change of state _offset_ requests a new portion of characters.
- CharInfo: A sidebar that displays information about the selected character. The information is queried by the Marvel API when the user clicks on the corresponding character in the CharList. Information: name, short description (max 210 characters), as well as a list of comics (by clicking on any of them, you will go to the page of the corresponding comic).
- CharSearchForm: Formik and Yup libraries are involved. This is a form to search for the desired character in the Marvel API database. If the character is found, you will be prompted to go to the page about him. Otherwise, it will be reported on its absence.
#### More on ComicPage
Comic book list page. Card data comes from the Marvel API. By clicking on any of the cards, by ID, information about the comic will be requested and the user will go to the generated page.
 
