# jupyter-styling

Matplotlib stylesheet and Berkeley Haas brand color palettes, along with instructions for usage in Jupyter notebooks.

Note: Jupyter notebook stylesheet work on hold pending Jupyter UI accessibility updates.

<ol>
  <li><a href='#motive'>Motivation</a>
    <ol><li><a href="#access">Accessibility</a>
        <ul><li><a href="#notes">Notes on accessibility</a></li></ul>
        </li>
        <li><a href="#brand">Branding</a>
        </li>
      </ol>
  <li> <a href="#install">Local Installation</a>
    <ol><li> <a href="#fonts">Install fonts</a></li>
        <li> <a href="#style">Install stylesheet</a></li>
    </ol>
  </li>
  
  </li></ol>

------------
## <a name='motive'>Motivation</a>
This stylesheet was developed with two goals in mind:
- increase graph accessibility by default with minimum user effort
- brand graphs for Haas Berkeley

### <a name='access'>Accessibility</a>
Notable default features included in the stylesheet:

- figure
  - increased figure size
  - AA contrast-compliant background grid
  - increased title and axis label sizes
- color palette
  - each color passes AA contrast compliance with regard to the default background
  - colors were chosen to maximize contrast for colorblindness with one another (within Berkeley brand colors)
- scatter plots
  - points have a border to increase contrast with overlapping points
- line plots
  - line styles vary automatically with color

#### <a name='notes'>Notes on accessibility</a>
While this stylesheet makes graphs more accessible in many cases, users should still expect that graphs will need 
 additional style tweaks at the time the code is written in order to achieve WCAG 2.0 compliance. Notable things
that could NOT be automated in this stylesheet:

- as of Matplotlib 3.5.0, it is not possible to do the following things via stylesheet:
  - automatically cycle through scatter plot point shape with color
  - automatically cycle through bar graph hatch patterns with color
  - add contrasting borders between bar graph bars
There are also some limitations that come from Haas branding:
  - color palette colors may not be discernible in grayscale or for users with achromatopsia. 
  Recommend using the matplotlib built-in grayscale palette instead.

We recommend using thinking of this stylesheet as an accessibility aid and not an all-in-one
solution. Complementary best practices include:
- Avoiding conveying meaning with color alone 
  - Labeling lines, bars, axes, etc
  - Manually changing scatter plot point shape for different categories with the `marker` parameter
- Providing screenreader-friendly tables alongside graphs that convey the same information
- Writing alt text for graphs exported as images

### <a name='brand'>Haas Berkeley branding</a>
- Haas Berkeley brand colors in palette, titles/labels, and axes
- 'Roboto' default font

--------
## <a name='install'>Local Installation</a>
### <a name='fonts'>Install Fonts</a>
The stylesheets use Roboto. Note: all fonts must be in ttf format to be used in Matplotlib.

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

### <a id='style'>Install Matplotlib Stylesheet</a>
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

Code and README maintained by Keeley Takimoto (ktakimoto@berkeley.edu). Enormous thanks to Amy Ho for her work on 
Berkeley branding and colorblind accessibility.