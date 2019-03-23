diff --git a/asterisk_head/main/app.c b/asterisk/main/app.c
index d272e40..3a9f633 100644
--- a/asterisk_head/main/app.c
+++ b/asterisk/main/app.c
@@ -922,13 +922,14 @@ static int dtmf_stream(struct ast_channel *chan, const char *digits, int between
                                break;
                        }
                } else if (strchr("0123456789*#abcdfABCDF", *ptr)) {
-                       if (*ptr == 'f' || *ptr == 'F') {
-                               /* ignore return values if not supported by channel */
-                               ast_indicate(chan, AST_CONTROL_FLASH);
-                       } else {
-                               /* Character represents valid DTMF */
-                               my_senddigit(chan, *ptr, duration);
-                       }
+                       my_senddigit(chan, *ptr, duration);
+               //      if (*ptr == 'f' || *ptr == 'F') {
+               //              /* ignore return values if not supported by channel */
+               //              ast_indicate(chan, AST_CONTROL_FLASH);
+               //      } else {
+               //              /* Character represents valid DTMF */
+               //              my_senddigit(chan, *ptr, duration);
+               //      }
                        /* pause between digits */
                        res = my_sleep(chan, between);
                        if (res) {
