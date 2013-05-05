liang-barsky-in-c
=================

Just a simple Liang-Barsky line clipping algorithm implemented in C

Adapted from Hin Jang's C++ implementation found here:
http://hinjang.com/articles/04.html#eight

Interface looks like this:

    struct liang_barsky_clip_window {
    	float x1, y1, x2, y2;
    };

clip_line()
 * modifies parameters in place to clip the line,
 * returns 0 if line is totally outside clip window
 * returns 1 if line is not totally outside clip window

    int clip_line(struct liang_barsky_clip_window *c,
    			int *x1, int *y1, int *x2,  int *y2);

clip_line_copy()
 * first four coords are input line coords
 * last four coords are clipped output line coords
 * returns 0 if line is totally outside clip window
 * returns 1 if line is not totally outside clip window

    int clip_line_copy(struct liang_barsky_clip_window *c,
    			int x1, int y1, int x2, int y2,
    			int *ox1, int *oy1, int *ox2, int *oy2);

Use it like this:

    /* set up clip windows */
    struct liang_barsky_clip_window my_clip_window = { 0, 0, 800, 600 };

    /* draw some lines */
    int x1, y1, x2, y2;
    
    x1 = some_random_number();
    y1 = some_random_number();
    x2 = some_random_number();
    y2 = some_random_number();
    if (clip_line(&my_clip_window, &x1, &y1, &x2, &y2))
        draw_line(x1, y1, x2, y2);

