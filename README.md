liang-barsky-in-c
=================

Just a simple Liang-Barsky line clipping algorithm implemented in C

Adapted from Hin Jang's C++ implementation found here:
http://hinjang.com/articles/04.html#eight

struct liang_barsky_clip_window {
	float x1, y1, x2, y2;
};

/* clip_line()
 * modifies parameters in place to clip the line,
 * returns 0 if line is totally outside clip window
 * returns 1 if line is not totally outside clip window
 */
GLOBAL int clip_line(struct liang_barsky_clip_window *c,
			int *x1, int *y1, int *x2,  int *y2);

/* clip_line_copy()
 * first four params are input line coords
 * last four params are clipped output line coords
 * returns 0 if line is totally outside clip window
 * returns 1 if line is not totally outside clip window
 */
int clip_line_copy(struct liang_barsky_clip_window *c,
			int x1, int y1, int x2, int y2,
			int *ox1, int *oy1, int *ox2, int *oy2);

