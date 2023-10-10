![Pygame](https://www.pygame.org/docs/_images/pygame_logo.png)

# TRULY CENTERED BUTTON CLASS
**Sick and tired of Pygame's uncentered text on your buttons? Look no further!**

`my_button = Button(params)`

## Required parameters
- **screen**: `pygame.Surface`
- **text**: `str`
- **color**: `tuple` `(r, g, b)`
- **center**: `tuple` `(x, y)`
- **dim**: `tuple` `(w, h)`

## Optional parameters
- **thickness**: `int`
- **radius**: `int`
- **font_size**: `int`

## Additional Attributes
- **real_rect**: Actual surrounding border seen on screen
- **font_rect**: Invisible border that wraps the text
- **screen_color**: Screen color behind the button
- **clicked**: Returns whether the button has been clicked

## Methods
- **draw()**: Draws the button (recommended to run immediately after instantiation)
- **is_hovered()**: Checks if button is hovered (does not update visual state)
- **is_clicked()**: Updates visual state of button and returns whether the button was just clicked

## Quickstart
### shell
```
pip install pygame-truly-centered-button
```

### python
```
#example.py

import pygame
from pgcenteredbutton import Button, BadButton 

if __name__ == "__main__":
    
    pygame.init()
    clock = pygame.time.Clock()

    screen = pygame.display.set_mode((1000, 1000))
    button_color = (200, 200, 200)
    button_center = (350, 500)
    button_dim = (300, 100)
    
    good_button = Button(screen = screen, text = 'GOOD', color = button_color, center = button_center, dim = button_dim)
    good_button.draw()

    bad_button_center = (650, 500)
    bad_button = BadButton(screen = screen, text = 'BAD', color = button_color, center = bad_button_center, dim = button_dim)
    bad_button.draw()

    while good_button.clicked is False:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                exit()

            if good_button.is_clicked(event):
                print('goodbye world')
                
        clock.tick(60)
        pygame.display.update()
    
    pygame.quit()
    exit()
```

