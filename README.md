# jupyter-styling

Matplotlib stylesheet and Berkeley Haas brand color palettes, along with instructions for usage in Jupyter notebooks.


## Local Installation

### Install Fonts
The stylesheets use Roboto. Note: all Matplotlib fonts must be in ttf format.

1. If Jupyter Notebook is running, stop it.
2. [Download Roboto](https://fonts.google.com/specimen/Roboto)
3. Install Roboto on your system. For most systems, clicking on each ttf file will give you an option to start installation.
4. Open up a terminal window and clear the Matplotlib cache by running `rm -fr ~/.cache/matplotlib`
5. You can check that Roboto is findable by Matplotlib using the following commands:

<pre>
# get a list of all Matplotlib fonts
import matplotlib.font_manager 
matplotlib.font_manager.findSystemFonts(fontpaths=None, fontext='ttf')
</pre>

<pre>
# look for Roboto using Matplotlib
from matplotlib import font_manager
font_manager.findfont('Roboto')
</pre>

### Install Matplotlib Stylesheet
Place the `haas-light.mplstyle` and `haas-dark.mplstyle` files into the Matplotlib style library at `mpl_configdir/stylelib`. By default 
`mpl_configdir` should be in `~/.config/matplotlib`, but you can check where yours is with `matplotlib.get_configdir()` 
(you may need to create the directory). You also can change the directory where Matplotlib looks for the `stylelib/`
folder by setting the MPLCONFIGDIR environment variable, see [matplotlib configuration and cache directory locations](
https://matplotlib.org/stable/users/faq/troubleshooting_faq.html#locating-matplotlib-config-dir).

If the stylesheet is in the right place, the following command should be `True`:
`'haas-light' in plt.style.available`

Once `haas-light.mplstyle` is in the appropriate location, you can specify your style with:

`import matplotlib.pyplot as plt`
`plt.style.use('haas-dark')`
