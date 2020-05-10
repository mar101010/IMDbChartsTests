# IMDb Top Rated Movies Tests 

## How to run the tests
  
The tests are written in Java and managed by Maven project management tools. The project name is "ImdbTopRatedMovies".
1. To install and configure Maven please refer to following article, it contains instruction for Windows, Linux and Mac: https://www.baeldung.com/install-maven-on-windows-linux-mac
2. In Java class "ImdbTopRatedMoviesPage" of mentioned project, in the same-named constructor all Chrome drivers pathes are specified (for Windows, for Linux and for Mac). Please uncomment one depending on your OS. Chrome driver for Windows is un-commented by default.  
3. Run "mvn clean test" command in terminal or cmd from the root folder of the commit or from project folder (if you use Intellij, Exlipse etc).
Should you have any questions feel free to email me!

## Tests
#### All tests are peformed from "Top Rated Movies" page: https://www.imdb.com/chart/top?ref_=nv_mv_250_6
#### In the contect of testing I call "IMDb Charts" column "section", column's items (including "Top Rated Movies") are called "divisions". Tests are ordered as per higher->lower priority. Testcases related to "Top Rated Movies" have the highest priorities, then movies detailed view, other divisions and "Box Office" division in the end.

1 - "Sort by:" is set "Ranking" by default in "Top Rated Movies",all items are sorted accordingly and have relevant order numbers

2 - It is possible to open any movie, the movie title and all data is correct

3 - Signing in the system from "Top Rated Movies" user stays on the same page
Bug! Sometimes user is redirected to homepage

4 - All texts are correct in "Top Rated Movies"
Bug! there is no headers for the columns of "Poster" and "Add to Watchlist"

5 - Changing the sorting criterions items are sorted
accordingly (both ascending and descending), but order numbers stay according to default "Ranking" sorting

6 - Logged user can set its own rating for an item from movies items list and update it

7 - Logged user can mark and unmark the item as "seen" in movies items list

8 - Logged user can add the item to Watchlist from movie items list and remove, view via username -> your Watchlist menu

9 - It is possible to share "Top Rated Movies" in different ways
Bug! Email sharing does not work

10 - "Top Rated Movies" clickable elements have all required tooltips
Bug! no tooltips for Posters and for Ratings

11 - Logged user can set its own rating for any movie from movie detailed view and update it

12 - Logged user can add the item to Watchlist from movie detailed view top left icon (and make sure this icon is synchronyzed with
 "Add to Watchlist" lower icon) and remove, view via "View Watchlist" (menu appears navigating to the icon)
Bug! Add to Watchlist icons in item view are not synchronyzed with each other

13 - Logged user can add the item to Watchlist from movie detailed view "Add to Watchlist" lower icon and remove,
view via newly appeared "Watchlist" tab and make sure it has a marker with number of items

14 - Logged user can add the item to his own lists from movie detailed view top left icon

15 - Switching between different divisions of "IMDb Charts" all texts stay the same, only Header and Summary changes accordingly

16 - "IMDb Charts" section is always seen from any other divisions
Bug! "IMDb Charts" section is not seen from "Top Rated Indian Movies"

17 - All divisions (apart from "Box Offices") have the same view and functionality as "Top Rated Movies" (tests 1-10, bugs are relevant)

18 - "Box Office" division has correct texts

19 - Correct money $ amount is displayed for all "Box Office" items

20 - "Box Office" division has all required tooltips
! no tooltip for Poster, see bug in test 10


## Test cases to be added to smoketest:
#### 1, 2, 3, 5, 6, 12, 16, 19
#### These tests most probably have dependencies on other modules and components. As you have see, we have vew testcases for the same functionality from different views (e.g. 8, 12 and 13 for "Add to Watchlist"). It such cases I take only one test for smoketest.

## Two tests (#4 and #8) are automated and described in a detailed way below 

### 4 -  All texts are correct in "Top Rated Movies"

Preconditions:
1. "Top Rated Movies" division of "IMDb Charts" section is open

Steps:
1. Make sure that all common texts of the IMDb Chart's view are correct:
- Article: "IMDb Charts"
- Header: "Top Rated Movies"
- Summary: "Top 250 as rated by IMDb Users"
- Share: "SHARE"
- Description: "Showing 250 Titles"
- Sorting menu: "Sort by:"
- Columns: "Poster", "Rank & Title", "IMDb Rating", "Your Rating", "Add to Watchlist"

Expected: All the texts of "Top Rated Movies" divisiton have correct names

### 8 - Logged user can add the item to Watchlist in items list

Preconditions:
1. User is signed in
2. "Top Rated Movies" division of "IMDb Charts" section is open
3. Some movies items are available in the list below

Steps:
1. Click on "+" icon near any two movies (item1 and item2) to add it to Watchlist
2. Remember the movies titles
3. Make sure the icon style near the movies is changed accordingly
4. Click on checked icon near any of two movies (e.g. item1) to remove it from Watchlist
5. Make sure the icon style near the item1 is changed accordingly
6. Open user's watchlist (username top-right corner -> dropdown menu -> Your watchlist)
7. Make sure that newly added item2 is in the watchlist
8. Remove item2 from the Watchlist and refresh the browser
9. Make sure item2 is disappeared from Watchlist

Expected: Selected item is successfully added to Watchlist and removed

Postconditins: user is signed out
