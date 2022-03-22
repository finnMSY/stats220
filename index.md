# Project 1
## Summary
In this part of the project I was tasked to construct a meme out of different images using the `R` programming language and a function of `R` called `magick`.

## The Meme
The meme I created was based of the 'A Fellow Man of Culture' meme template. I chose this for a few reason:
1. The meme has a grid like structure which allows me to showcase certain `magick` functions such as `image_blank`, `image_read`, and `image_append`.
2. It's realitively simple to make and a good first project using `R`
3. It has a very clear and effective meaning which is easily identified.

>*This meme originated as a reaction image on a website called [**4chan**](https://www.4channel.org/)
>The reaction image was:
![Tuxedo Winnie the Pooh](https://i.kym-cdn.com/entries/icons/original/000/029/060/cover3.jpg)*

### Here is the created meme:

![An 'A Fellow Man of Culture' meme with the text 'studying compsci and stats in the first column', and 'studying datascience' in the second](meme.png)

## The Process
I used the following code to create this meme:
```diff
library(magick)

# image one
normal_poobear <- image_read("https://i.kym-cdn.com/photos/images/original/001/474/942/012.gif") %>%
  image_scale("500x500!")

# image two
cool_poobear <- image_read("https://en.meming.world/images/en/8/89/Tuxedo_Winnie_the_Pooh.jpg") %>%
  image_scale("500x500!")

# word square one
compsci_stats_text <- image_blank(width=500, height=500, color="#000000") %>%
  image_annotate(text="Studying\nStats and Compsci", color="#FFFFFF", size=50, font="serif", gravity="center")

# word square two
datasci_text <- image_blank(width=500, height=500, color="#000000") %>%
  image_annotate(text="Studying\nDatascience", color="#FFD700", size=50, font="Impact", gravity="center")

# creating the first row
first_row_vector <- c(normal_poobear, compsci_stats_text)
first_row <- image_append(first_row_vector)

# creating the second row
second_row_vector <- c(cool_poobear, datasci_text)
second_row <- image_append(second_row_vector)

# creating the whole meme
meme_vector <- c(first_row, second_row)
meme <- image_append(meme_vector, stack=TRUE)
image_write(meme, "Images/meme.png")
```
---
>This code creates the meme image with this specific code creating the individual squares

```diff
# image one
normal_poobear <- image_read("https://i.kym-cdn.com/photos/images/original/001/474/942/012.gif") %>%
  image_scale("500x500!")

# image two
cool_poobear <- image_read("https://en.meming.world/images/en/8/89/Tuxedo_Winnie_the_Pooh.jpg") %>%
  image_scale("500x500!")

# word square one
compsci_stats_text <- image_blank(width=500, height=500, color="#000000") %>%
  image_annotate(text="Studying\nStats and Compsci", color="#FFFFFF", size=50, font="serif", gravity="center")

# word square two
datasci_text <- image_blank(width=500, height=500, color="#000000") %>%
  image_annotate(text="Studying\nDatascience", color="#FFD700", size=50, font="Impact", gravity="center")
```

>This code combining the squares together:

```diff
# creating the first row
first_row_vector <- c(normal_poobear, compsci_stats_text)
first_row <- image_append(first_row_vector)

# creating the second row
second_row_vector <- c(cool_poobear, datasci_text)
second_row <- image_append(second_row_vector)

# creating the whole meme
meme_vector <- c(first_row, second_row)
meme <- image_append(meme_vector, stack=TRUE)
image_write(meme, "Images/meme.png")
```
