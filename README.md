Highlight selected word
=======================

[![Join the chat at https://gitter.im/jcb91/jupyter_highlight_selected_word](https://badges.gitter.im/jcb91/jupyter_highlight_selected_word.svg)](https://gitter.im/jcb91/jupyter_highlight_selected_word?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![GitHub issues](https://img.shields.io/github/issues/jcb91/jupyter_highlight_selected_word.svg?maxAge=3600)](https://github.com/jcb91/jupyter_highlight_selected_word/issues)

[![GitHub tag](https://img.shields.io/github/tag/jcb91/jupyter_highlight_selected_word.svg?maxAge=3600&label=Github)](https://github.com/jcb91/jupyter_highlight_selected_word/tags)
[![PyPI](https://img.shields.io/pypi/v/jupyter_highlight_selected_word.svg?maxAge=3600)](https://pypi.python.org/pypi/jupyter_highlight_selected_word)
[![Anaconda cloud](https://anaconda.org/conda-forge/jupyter_highlight_selected_word/badges/version.svg)](https://anaconda.org/conda-forge/jupyter_highlight_selected_word)


Enables the CodeMirror addon [Match Highlighter](https://codemirror.net/demo/matchhighlighter.html),
which highlights all instances of the selected word in the current editor.

There are a few configurable options, all of which sit under the config key
`highlight_selected_word` in the `notebook` config section.


Installation
------------

`jupyter_highlight_selected_word` is available as part of the
[jupyter_contrib_nbextensions](https://github.com/ipython-contrib/jupyter_contrib_nbextensions)
collection. If you want to install this nbextension without the rest of the
contrib collection, read on.

To use the nbextension, there are three basic steps:

1.  First, install the python package:

        pip install jupyter_highlight_selected_word

    Or, __for those using conda__, there is now a recipe provided through the
    excellent
    [conda-forge]()
    [channel](),
    which also performs the install into the conda env's jupyter data
    directory, so you can skip step 2. To install the conda recipe, use

        conda install -c conda-forge jupyter_highlight_selected_word

2.  Next, install javascript files from the python package into a jupyter data
    directory.

    If you have jupyter version 4.2 or greater, you can install directly
    using jupyter:

        jupyter nbextension install --py jupyter_highlight_selected_word

    For jupyter versions before 4.2, you'll need to do a little more work to
    find the nbextension's static files. To find the nbextension source
    directory, you can use the following one-liner
    (for a rather stretched definition of 'line'):

        python -c "import os.path as p; from jupyter_highlight_selected_word import __file__ as f, _jupyter_nbextension_paths as n; print(p.normpath(p.join(p.dirname(f), n()[0]['src'])))"

    then execute

        jupyter nbextension install <output source directory>

    replacing `<output source directory>` with the directory found above.


3.  Enable the nbextension, so that it gets loaded automatically in each
    notebook:

        jupyter nbextension enable highlight_selected_word/main


Options
-------

Options are stored in the notebook section of the nbconfig.
The easiest way to configure these is using the
[jupyter_nbextensions_configurator](https://github.com/Jupyter-contrib/jupyter_nbextensions_configurator)
serverextension, but you can also configure them directly with a few lines of
python.

The available options are:

* `highlight_selected_word.code_cells_only` - Only apply highlights to editors
  for Code cells, not, for example, Markdown or Raw cells
* `highlight_selected_word.highlight_color` - Color to highlight matching words
* `highlight_selected_word.delay` - Wait time (in milliseconds) before
  highlighting the matches
* `highlight_selected_word.words_only` - If true, only highlight matches if the
  selected text is a word
* `highlight_selected_word.min_chars` - Minimum number of characters that must
  be selected for the highlighting behavior to occur
* `highlight_selected_word.show_token` - Token (regex) to highlight when
  nothing is selected

For example, to set the delay to half a second, and limit higlighting to code
cells, we can use the following python snippet:

```python
from notebook.services.config import ConfigManager
cm = ConfigManager()
cm.update('notebook', {'highlight_selected_word': {
    'delay': 500,
    'code_cells_only': True,
}})
```


Feedback
--------

If you have any feedback, or have any problems, please let me know by
[opening an issue](https://github.com/jcb91/jupyter_highlight_selected_word/issues/new)
at the project's
[github repository](https://github.com/jcb91/jupyter_highlight_selected_word).

Thanks!

Josh.
