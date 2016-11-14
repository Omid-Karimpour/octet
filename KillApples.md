## Kill the Apples

I had never worked with C++ before but during my under graduate studies I was taught Java. Having studied at least one form of object oriented programming, I was able to understand some parts of C++. I decided first to change the looks of the sprite. I first change the invader size and by editing the following line of code:

   invaderer, ((float)i - num_cols * 0.5f) * 0.5f, 2.50f - ((float)j * 0.5f), 0.50f, 0.50f

I then changed the image so the invaders will look like apples. Just replaced the invader.gif file in the assets folder.

My next step was to create the ending of the game. First I added a new image for R.I.P. 
 
I then had made a restart option to the game so once you had died, you just press the backspace button and the game will restart. I did this within the draw the world section of the coding:
// this is called to draw the world
    void draw_world(int x, int y, int w, int h) {
      simulate();

	  if (You_Died && is_key_going_up(key_backspace))
	  {
		  app_init();
		  return;

	  }

      // set a viewport - includes whole window area
      glViewport(x, y, w, h);
      
I also changed the background colour to cyan by editing the following:

glClearColor(0, 5, 5, 5);
      glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);


Next I changed the border colour from white to black by making the following changes:

// set the border to white for clarity
      GLuint white = resource_dict::get_texture_handle(GL_RGB, "#111111");
      
      // up and down arrows
	  if (is_key_down(key_up)) { 
		  sprites[ship_sprite].translate(0, +ship_speed);
	  if (sprites[ship_sprite].collides_with(sprites[first_border_sprite + 1])) { 
		  sprites[ship_sprite].translate(0, -ship_speed);
	    } 
	  }
	  else if (is_key_down(key_down)) {
		  sprites[ship_sprite].translate(0, -ship_speed);
		  if (sprites[ship_sprite].collides_with(sprites[first_border_sprite + 0])) {
			  sprites[ship_sprite].translate(0, +ship_speed);
		  }
	  }
	  
Contact GitHub API Training Shop Blog About
© 2016 GitHub, Inc. Terms Privacy Security Status Help
