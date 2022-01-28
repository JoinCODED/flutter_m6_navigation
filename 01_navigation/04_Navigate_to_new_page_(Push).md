We already created a new page, now we will need to learn how to move from the home page to the movie page.

15. The first step is we want to specify when we will need to move to the new page, in our case we need to go to the movie page when the user clicks the movie tile. So, we will use the **InkWell** widget to add the **onTap** event on the movie tile, which has the same functionality as the **GestureDetector** widget, but with a nice animation effect ^\_^.

![screenshot](https://lh6.googleusercontent.com/kot72_5VKV2laZStWICfrg8W0ZjJdyL_RVW6F00Tj68yEjD9q7ocgcN4t3beCCd9QMF1eQl07zW04JTJinzOhO7DWhZ0b4dVVOtlDTG-uimdJ-v6fYrm7z0CaE3bmTIAO-CtTDKI)

Wrap the Row widget with the **InkWell** widget.

> **Note:** We added the **onTap** event named argument; we will add the logic that responsible for moving to a new page in this event.

```dart
InkWell(      // <- Here
              onTap: () {},
              child: Row(
                children: [
                  Expanded(
                    child: Container(
                      padding: EdgeInsets.all(10),
                      child: Column(
                        children: [
                          Text(
                            '${movies[index].name}',
                            style: TextStyle(
                              fontWeight: FontWeight.bold,
                              fontSize: 18,
                            ),
                          ),
                          Container(height: 10),
                          Text(
                            'Rating: ${movies[index].rating}/10',
                            style: TextStyle(
                              fontWeight: FontWeight.bold,
                              color: Colors.grey[700],
                              fontSize: 14,
                            ),
                          ),
                        ],
                      ),
                    ),
                  ),
                  Container(
                    padding: EdgeInsets.all(10),
                    child: Image.asset(
                      movies[index].imgPath, // <- Here
                      width: 125,
                      height: 125,
                    ),
                  ),
                ],
              ),
            ),
```

1.  Before we learn how to move to the new page, we will need to understand how the Navigator used the stack inside Flutter.

![screenshot](https://lh6.googleusercontent.com/9j26ZwF5PsAngBZSIryDVKsTNUdQ0WjAJrvms2gu2PlCh46Tloblb_yGOqowMnqFIwk0J24P6due0dlF_6SUeOlU2r_mcs45mHth8aWzfHLWTToHLMbcF_-HbsqS_doIkkn-VXzm)

You can imagine the Navigator as the **Stack** that contains multiple pages, and the first top page inside the stack is the page that the user will see it.

17. To move to the new page, we will call the **Navigator.push()** method inside the **onTap** event, then we will pass the page which you want to show.

    ```dart
     onTap: () {
                    // 1
                    Navigator.push(
                      // 2
                      context,
                      MaterialPageRoute(
                        // 3
                        builder: (context) => MoviePage(),
                      ),
                    );
                  },
    ```

1. Here, we used the **Navigator.push** method to show the Movie Page widget.
1. To use the **push** method, you will need to pass the **context** object first.
1. Here you tell Flutter which screen you will need to display. In our case, we show the **MoviePage** widget that we created before.

1. Don’t forget to import the **movie_page.dart** inside the **home_page.dart** file, because we called it inside the **Navigator.push** method.

   ```dart
   import 'package:flutter_movie_app_starter/pages/movie_page.dart';
   ```

1. Now, try to restart the app, and click one of the movie tiles. ^\_^.

![screenshot](https://user-images.githubusercontent.com/24327781/142048432-eb1dd37c-c0ed-449a-a4f4-aa51e5320bfc.gif)
