Readme.txt for  Anaconda Python 3 install of https://github.com/shantnu/PyEng
29-Apr-2017
David Dorff
davidd639@yahoo.com

Environment:  Ubuntu 16.04.2; installed in AWS EC2 (Free tier)
Python executable: /home/ubuntu/anaconda3/bin/python

File: audio/create_wave.py
Error: ModuleNotFoundError: No module named 'PyQt4'
Probable cause: Issue explained in github link: https://github.com/ContinuumIO/anaconda-issues/issues/1068
Fresh matplotlib install broken: installs qt5, but matplotlib rc patched to require qt4 #1068

File: audio/get_freq.py
Error: ModuleNotFoundError: No module named 'PyQt4'
Probable cause: See above with github link #1068 for explanation

File: audio/noisy.py
Error: ModuleNotFoundError: No module named 'PyQt4'
Probable cause: See above with github link #1068 for explanation

File: Image_Video/blur.py
Error: ModuleNotFoundError: No module named 'cv2'
Probable cause: Issue explained in github link: https://github.com/05dirnbe/nefi/issues/31
No module named 'cv2' #31
Solution involves installing the OpenCV package

File: Image_Video/color_test.py
Error: ModuleNotFoundError: No module named 'SimpleCV'
Probable cause:  Not sure, but it looks like SimpleCV needs to be installed as an additional step.

File: Image_Video/color_train.py
Error: ModuleNotFoundError: No module named 'SimpleCV'
Probable cause:  Not sure, but it looks like SimpleCV needs to be installed as an additional step.

File: Image_Video/count_cards.py
Error: ModuleNotFoundError: No module named 'cv2'
Probable cause: See above with github link #31 for explanation

File: Image_Video/display.py
Error: ModuleNotFoundError: No module named 'cv2'
Probable cause: See above with github link #31 for explanation

File: Image_Video/edge_detect.py
Error: ModuleNotFoundError: No module named 'cv2'
Probable cause: See above with github link #31 for explanation

File: Image_Video/face_detect.py
Error: ModuleNotFoundError: No module named 'cv2'
Probable cause: See above with github link #31 for explanation

File: Image_Video/motion_detect.py
Error: ModuleNotFoundError: No module named 'cv2'
Probable cause: See above with github link #31 for explanation

File: Image_Video/webcam_face_detect.py
Error: ModuleNotFoundError: No module named 'cv2'
Probable cause: See above with github link #31 for explanation
File: machine/calc_correlation.py
Error: SyntaxError: Missing parentheses in call to 'print'
Probable cause: Confirmed that adding parens () around print arguments solves the problem.  Note that, since this script expects a file name as argument, I found that if the argument isn't an existing file (as was the case with a typo), the script throws a FileNotFound Error.

File: machine/corr_dict.py
OK

File: machine/ml_data1.py
OK

File: machine/ml_main.py
Error: SyntaxError: Missing parentheses in call to 'print'
Probable cause: Confirmed that adding parens () around print arguments solves the problem.

File: Multiprocessing/gen_rand.py
Error: SyntaxError: Missing parentheses in call to 'print'
Probable cause: Confirmed that adding parens () around print arguments solves the problem.

File: Multiprocessing/process.py
Error: SyntaxError: Missing parentheses in call to 'print'
Probable cause: Confirmed that adding parens () around print arguments solves the problem.  Note that the error wasn't in process.py, but in gen_rand.py, which is called from within.

File: Multiprocessing/single.py
Error: SyntaxError: Missing parentheses in call to 'print'
Probable cause: Confirmed that adding parens () around print arguments solves the problem.  Note that the error wasn't in single.py, but in gen_rand.py, which is called from within.

File: Multiprocessing/thread.py
Error: SyntaxError: Missing parentheses in call to 'print'
Probable cause: Confirmed that adding parens () around print arguments solves the problem.  Note that the error wasn't in process.py, but in gen_rand.py, which is called from within.


File: Pandas/obesity.py
Error: SyntaxError: Missing parentheses in call to 'print'
Probable cause: Confirmed that adding parens () around print arguments solves the problem.  Note that, once solved, it moves on to generate the ModuleNotFoundError: No module named 'PyQt4', discussed above.


File: Pandas/pandas_movie.py
Error: SyntaxError: invalid syntax
Probable cause: Confirmed that adding parens () around print arguments solves this problem.  Note that, once solved (and after adding parens around all print statements in the module), it moves on to generate the ModuleNotFoundError: No module named 'PyQt4', discussed above

File: Plotting/data_plot.py
Error: ModuleNotFoundError: No module named 'PyQt4'
Probable cause: See above with github link #1068 for explanation

File: Plotting/graph_wave.py
Error: ModuleNotFoundError: No module named 'PyQt4'
Probable cause: See above with github link #1068 for explanation

File: Plotting/list_comp.py
OK

File: rpi/hello.py
OK

File: rpi/webapp_bootstrap.py
Error: PermissionError: [Errno 13] Permission denied
Probable cause:  Confirmed permission item can be solved by running as superuser:
    sudo /home/ubuntu/anaconda3/bin/python webapp.py
error was at line 691, s.bind(), from ~/anaconda3/lib/python3.6/site-packages/werkzeug/serving.py
    # Create and destroy a socket so that any exceptions are
    # raised before we spawn a separate Python interpreter and
    # lose this ability.
    address_family = select_ip_version(hostname, port)
    s = socket.socket(address_family, socket.SOCK_STREAM)
    s.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
    s.bind((hostname, port))
Stack Overflow had info
https://stackoverflow.com/questions/43471452/permissionerror-errno-13-permission-denied-file-python3-5-site-packages-werk
http://stackoverflow.com/questions/38298652/permissionerror-errno-13-permission-denied-flask-run


File: rpi/webapp.py
Error: PermissionError: [Errno 13] Permission denied
Probable cause:  Confirmed permission item can be solved by running as superuser.  See same explanation above, for webapp_bootstrap.py

File: WordCount/count_lines_fixed.py
OK

File: WordCount/count_words.py
OK

File: WordCount/read_file.py
OK

File: WordCount/word_count.py
OK



-----------------
Checking files in directory audio
File: audio/create_wave.py

-rw-rw-r-- 1 ubuntu ubuntu 828 Apr 21 23:44 create_wave.py

Traceback (most recent call last):
  File "create_wave.py", line 4, in <module>
    import matplotlib.pyplot as plt
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/pyplot.py", line 115, in <module>
    _backend_mod, new_figure_manager, draw_if_interactive, _show = pylab_setup()
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/__init__.py", line 32, in pylab_setup
    globals(),locals(),[backend_name],0)
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/backend_qt5agg.py", line 16, in <module>
    from .backend_qt5 import QtCore
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/backend_qt5.py", line 26, in <module>
    import matplotlib.backends.qt_editor.figureoptions as figureoptions
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_editor/figureoptions.py", line 20, in <module>
    import matplotlib.backends.qt_editor.formlayout as formlayout
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_editor/formlayout.py", line 56, in <module>
    from matplotlib.backends.qt_compat import QtGui, QtWidgets, QtCore
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_compat.py", line 137, in <module>
    from PyQt4 import QtCore, QtGui
ModuleNotFoundError: No module named 'PyQt4'


File: audio/get_freq.py

-rw-rw-r-- 1 ubuntu ubuntu 782 Apr 21 23:44 get_freq.py

Traceback (most recent call last):
  File "get_freq.py", line 9, in <module>
    import matplotlib.pyplot as plt
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/pyplot.py", line 115, in <module>
    _backend_mod, new_figure_manager, draw_if_interactive, _show = pylab_setup()
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/__init__.py", line 32, in pylab_setup
    globals(),locals(),[backend_name],0)
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/backend_qt5agg.py", line 16, in <module>
    from .backend_qt5 import QtCore
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/backend_qt5.py", line 26, in <module>
    import matplotlib.backends.qt_editor.figureoptions as figureoptions
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_editor/figureoptions.py", line 20, in <module>
    import matplotlib.backends.qt_editor.formlayout as formlayout
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_editor/formlayout.py", line 56, in <module>
    from matplotlib.backends.qt_compat import QtGui, QtWidgets, QtCore
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_compat.py", line 137, in <module>
    from PyQt4 import QtCore, QtGui
ModuleNotFoundError: No module named 'PyQt4'


File: audio/noisy.py

-rw-rw-r-- 1 ubuntu ubuntu 2341 Apr 21 23:44 noisy.py

Traceback (most recent call last):
  File "noisy.py", line 9, in <module>
    import matplotlib.pyplot as plt
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/pyplot.py", line 115, in <module>
    _backend_mod, new_figure_manager, draw_if_interactive, _show = pylab_setup()
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/__init__.py", line 32, in pylab_setup
    globals(),locals(),[backend_name],0)
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/backend_qt5agg.py", line 16, in <module>
    from .backend_qt5 import QtCore
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/backend_qt5.py", line 26, in <module>
    import matplotlib.backends.qt_editor.figureoptions as figureoptions
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_editor/figureoptions.py", line 20, in <module>
    import matplotlib.backends.qt_editor.formlayout as formlayout
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_editor/formlayout.py", line 56, in <module>
    from matplotlib.backends.qt_compat import QtGui, QtWidgets, QtCore
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_compat.py", line 137, in <module>
    from PyQt4 import QtCore, QtGui
ModuleNotFoundError: No module named 'PyQt4'




Checking files in directory Image_Video
File: Image_Video/blur.py

-rw-rw-r-- 1 ubuntu ubuntu 376 Apr 21 23:44 blur.py

Traceback (most recent call last):
  File "blur.py", line 1, in <module>
    import cv2
ModuleNotFoundError: No module named 'cv2'


File: Image_Video/color_test.py

-rw-rw-r-- 1 ubuntu ubuntu 1423 Apr 21 23:44 color_test.py

Traceback (most recent call last):
  File "color_test.py", line 6, in <module>
    from SimpleCV import *
ModuleNotFoundError: No module named 'SimpleCV'


File: Image_Video/color_train.py

-rw-rw-r-- 1 ubuntu ubuntu 2470 Apr 21 23:44 color_train.py

Traceback (most recent call last):
  File "color_train.py", line 6, in <module>
    from SimpleCV import *
ModuleNotFoundError: No module named 'SimpleCV'


File: Image_Video/count_cards.py

-rw-rw-r-- 1 ubuntu ubuntu 662 Apr 21 23:44 count_cards.py

Traceback (most recent call last):
  File "count_cards.py", line 1, in <module>
    import cv2
ModuleNotFoundError: No module named 'cv2'


File: Image_Video/display.py

-rw-rw-r-- 1 ubuntu ubuntu 160 Apr 21 23:44 display.py

Traceback (most recent call last):
  File "display.py", line 1, in <module>
    import cv2
ModuleNotFoundError: No module named 'cv2'


File: Image_Video/edge_detect.py

-rw-rw-r-- 1 ubuntu ubuntu 505 Apr 21 23:44 edge_detect.py

Traceback (most recent call last):
  File "edge_detect.py", line 1, in <module>
    import cv2
ModuleNotFoundError: No module named 'cv2'


File: Image_Video/face_detect.py

-rw-rw-r-- 1 ubuntu ubuntu 641 Apr 21 23:44 face_detect.py

Traceback (most recent call last):
  File "face_detect.py", line 7, in <module>
    import cv2
ModuleNotFoundError: No module named 'cv2'


File: Image_Video/motion_detect.py

-rw-rw-r-- 1 ubuntu ubuntu 1145 Apr 21 23:44 motion_detect.py

Traceback (most recent call last):
  File "motion_detect.py", line 7, in <module>
    import cv2
ModuleNotFoundError: No module named 'cv2'


File: Image_Video/webcam_face_detect.py

-rw-rw-r-- 1 ubuntu ubuntu 931 Apr 21 23:44 webcam_face_detect.py

Traceback (most recent call last):
  File "webcam_face_detect.py", line 7, in <module>
    import cv2
ModuleNotFoundError: No module named 'cv2'




Checking files in directory machine
File: machine/calc_correlation.py

-rw-rw-r-- 1 ubuntu ubuntu 1798 Apr 21 23:44 calc_correlation.py

  File "calc_correlation.py", line 40
    print "Usage: python calc_correlation.py <data file.py>"
                                                           ^
SyntaxError: Missing parentheses in call to 'print'


File: machine/corr_dict.py

-rw-rw-r-- 1 ubuntu ubuntu 1200 Apr 21 23:44 corr_dict.py



File: machine/ml_data1.py

-rw-rw-r-- 1 ubuntu ubuntu 603 Apr 21 23:44 ml_data1.py



File: machine/ml_main.py

-rw-rw-r-- 1 ubuntu ubuntu 2084 Apr 21 23:44 ml_main.py

  File "ml_main.py", line 41
    print "total_my_votes = ", total_my_votes
                            ^
SyntaxError: Missing parentheses in call to 'print'




Checking files in directory Multiprocessing
File: Multiprocessing/gen_rand.py

-rw-rw-r-- 1 ubuntu ubuntu 155 Apr 21 23:44 gen_rand.py

  File "gen_rand.py", line 9
    print "job done"
                   ^
SyntaxError: Missing parentheses in call to 'print'


File: Multiprocessing/process.py

-rw-rw-r-- 1 ubuntu ubuntu 218 Apr 21 23:44 process.py

Traceback (most recent call last):
  File "process.py", line 3, in <module>
    from gen_rand import gen_random_data
  File "/home/ubuntu/DDPyEng/PyEng/Multiprocessing/gen_rand.py", line 9
    print "job done"
                   ^
SyntaxError: Missing parentheses in call to 'print'


File: Multiprocessing/single.py

-rw-rw-r-- 1 ubuntu ubuntu 170 Apr 21 23:44 single.py

Traceback (most recent call last):
  File "single.py", line 2, in <module>
    from gen_rand import gen_random_data
  File "/home/ubuntu/DDPyEng/PyEng/Multiprocessing/gen_rand.py", line 9
    print "job done"
                   ^
SyntaxError: Missing parentheses in call to 'print'


File: Multiprocessing/thread.py

-rw-rw-r-- 1 ubuntu ubuntu 205 Apr 21 23:44 thread.py

Traceback (most recent call last):
  File "thread.py", line 3, in <module>
    from gen_rand import gen_random_data
  File "/home/ubuntu/DDPyEng/PyEng/Multiprocessing/gen_rand.py", line 9
    print "job done"
                   ^
SyntaxError: Missing parentheses in call to 'print'




Checking files in directory Pandas
File: Pandas/obesity.py

-rw-rw-r-- 1 ubuntu ubuntu 1221 Apr 21 23:44 obesity.py

  File "obesity.py", line 5
    print  data.sheet_names
              ^
SyntaxError: Missing parentheses in call to 'print'


File: Pandas/pandas_movie.py

-rw-rw-r-- 1 ubuntu ubuntu 2024 Apr 21 23:44 pandas_movie.py

  File "pandas_movie.py", line 19
    print "Top rated movies (overall): \n" , movie_data.groupby('title').size().order(ascending=False)[:20]
                                         ^
SyntaxError: invalid syntax




Checking files in directory Plotting
File: Plotting/data_plot.py

-rw-rw-r-- 1 ubuntu ubuntu 875 Apr 21 23:44 data_plot.py

Traceback (most recent call last):
  File "data_plot.py", line 7, in <module>
    import matplotlib.pyplot as plt
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/pyplot.py", line 115, in <module>
    _backend_mod, new_figure_manager, draw_if_interactive, _show = pylab_setup()
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/__init__.py", line 32, in pylab_setup
    globals(),locals(),[backend_name],0)
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/backend_qt5agg.py", line 16, in <module>
    from .backend_qt5 import QtCore
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/backend_qt5.py", line 26, in <module>
    import matplotlib.backends.qt_editor.figureoptions as figureoptions
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_editor/figureoptions.py", line 20, in <module>
    import matplotlib.backends.qt_editor.formlayout as formlayout
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_editor/formlayout.py", line 56, in <module>
    from matplotlib.backends.qt_compat import QtGui, QtWidgets, QtCore
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_compat.py", line 137, in <module>
    from PyQt4 import QtCore, QtGui
ModuleNotFoundError: No module named 'PyQt4'


File: Plotting/graph_wave.py

-rw-rw-r-- 1 ubuntu ubuntu 534 Apr 21 23:44 graph_wave.py

Traceback (most recent call last):
  File "graph_wave.py", line 7, in <module>
    import matplotlib.pyplot as plt
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/pyplot.py", line 115, in <module>
    _backend_mod, new_figure_manager, draw_if_interactive, _show = pylab_setup()
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/__init__.py", line 32, in pylab_setup
    globals(),locals(),[backend_name],0)
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/backend_qt5agg.py", line 16, in <module>
    from .backend_qt5 import QtCore
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/backend_qt5.py", line 26, in <module>
    import matplotlib.backends.qt_editor.figureoptions as figureoptions
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_editor/figureoptions.py", line 20, in <module>
    import matplotlib.backends.qt_editor.formlayout as formlayout
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_editor/formlayout.py", line 56, in <module>
    from matplotlib.backends.qt_compat import QtGui, QtWidgets, QtCore
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/matplotlib/backends/qt_compat.py", line 137, in <module>
    from PyQt4 import QtCore, QtGui
ModuleNotFoundError: No module named 'PyQt4'


File: Plotting/list_comp.py

-rw-rw-r-- 1 ubuntu ubuntu 650 Apr 21 23:44 list_comp.py


Old fashioned way: x = [5, 10, 15, 20, 25] y = [1.0, 2.0, 3.0, 4.0, 5.0] 

List Comprehensions: x = [5, 10, 15, 20, 25] z = [1.0, 2.0, 3.0, 4.0, 5.0] 

No, you can't do that with regular Python lists

With Numpy: a = [ 5 10 15 20 25] b = [ 1.  2.  3.  4.  5.] 





Checking files in directory rpi
File: rpi/hello.py

-rw-rw-r-- 1 ubuntu ubuntu 315 Apr 21 23:44 hello.py

 *******  skipping hello.py 


File: rpi/webapp_bootstrap.py

-rw-rw-r-- 1 ubuntu ubuntu 621 Apr 21 23:44 webapp_bootstrap.py

Traceback (most recent call last):
  File "webapp_bootstrap.py", line 28, in <module>
    app.run(host='0.0.0.0', port=80, debug=True)
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/flask/app.py", line 841, in run
    run_simple(host, port, self, **options)
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/werkzeug/serving.py", line 691, in run_simple
    s.bind((hostname, port))
PermissionError: [Errno 13] Permission denied


File: rpi/webapp.py

-rw-rw-r-- 1 ubuntu ubuntu 618 Apr 21 23:44 webapp.py

Traceback (most recent call last):
  File "webapp.py", line 28, in <module>
    app.run(host='0.0.0.0', port=80, debug=True)
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/flask/app.py", line 841, in run
    run_simple(host, port, self, **options)
  File "/home/ubuntu/anaconda3/lib/python3.6/site-packages/werkzeug/serving.py", line 691, in run_simple
    s.bind((hostname, port))
PermissionError: [Errno 13] Permission denied




Checking files in directory WordCount
File: WordCount/count_lines_fixed.py

-rw-rw-r-- 1 ubuntu ubuntu 408 Apr 21 23:44 count_lines_fixed.py

Wrong: The number of lines is 10
Right: The number of lines is 8


File: WordCount/count_words.py

-rw-rw-r-- 1 ubuntu ubuntu 446 Apr 21 23:44 count_words.py

The words in the text are:
['STRAY', 'BIRDS', '\nBY', '\nRABINDRANATH', 'TAGORE', '\n\nSTRAY', 'birds', 'of', 'summer', 'come', 'to', 'my', '\nwindow', 'to', 'sing', 'and', 'fly', 'away.', '\n\nAnd', 'yellow', 'leaves', 'of', 'autumn,', 'which', '\nhave', 'no', 'songs,', 'flutter', 'and', 'fall', 'there', '\nwith', 'a', 'sigh.']
The number of words is  34
The lines in the text are:
['STRAY BIRDS ', 'BY ', 'RABINDRANATH TAGORE ', '', 'STRAY birds of summer come to my ', 'window to sing and fly away. ', '', 'And yellow leaves of autumn, which ', 'have no songs, flutter and fall there ', 'with a sigh.']
The number of lines is 10


File: WordCount/read_file.py

-rw-rw-r-- 1 ubuntu ubuntu 194 Apr 21 23:44 read_file.py

STRAY BIRDS 
BY 
RABINDRANATH TAGORE 

STRAY birds of summer come to my 
window to sing and fly away. 

And yellow leaves of autumn, which 
have no songs, flutter and fall there 
with a sigh.


File: WordCount/word_count.py

-rw-rw-r-- 1 ubuntu ubuntu 756 Apr 21 23:44 word_count.py

Usage: python word_count.py <file>




Done
