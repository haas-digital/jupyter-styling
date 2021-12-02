# jupyter-branding

Jupyter notebook stylesheet and Berkeley Haas brand color palettes, along with instructions for usage in Jupyter notebooks.


## Local Installation

### 1. Install Notebook Stylesheet
Place the `custom/` folder (which includes the stylesheet) in your Jupyter config folder, located by default at `~/.jupyter`. 

If you need to find your Jupyter config directories, you can run the following command from the command line:

<code>jupyter --config-dir</code>

### 2. Install Fonts
The stylesheets use Roboto. 

[Download Roboto](https://fonts.google.com/specimen/Roboto)

To get a list of all fonts findable by Matplotlib,run:

<code> import matplotlib.font_manager </code>
<code> matplotlib.font_manager.findSystemFonts(fontpaths=None, fontext='ttf')</code>

### 3. Install Matplotlib Stylesheet
Place the `haas-light.mplstyle` file into the Matplotlib style library at `mpl_configdir/stylelib`. By default 
`mpl_configdir` should be in `~/.config/matplotlib`, but you can check where yours is with `matplotlib.get_configdir()` 
(you may need to create the directory). You also can change the directory where Matplotlib looks for the `stylelib/`
folder by setting the MPLCONFIGDIR environment variable, see [matplotlib configuration and cache directory locations](
https://matplotlib.org/stable/users/faq/troubleshooting_faq.html#locating-matplotlib-config-dir).

If the stylesheet is in the right place, the following command should be `True`:
`'haas-light' in plt.style.available`

Once `haas-light.mplstyle` is in the appropriate location, you can specify your style with:

`import matplotlib.pyplot as plt`
`plt.style.use('haas-light')`
