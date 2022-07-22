# ⚡️ BLIP Research Poster Template 🔬

Bootstrapping Language-Image Pre-training for Unified Vision-Language Understanding and Generation

Use this app to share your research paper results. This app lets you connect a blogpost, arxiv paper, and a jupyter
notebook and even have an interactive demo for people to play with the model. This app also allows industry
practitioners to reproduce your work.

> The model demo is implemented using the official [BLIP](https://github.com/salesforce/BLIP) implementation by salesforce team.

## Getting started

### Installation

#### With Lightning CLI

`lightning install app lightning/icml22-blip`

#### Use GitHub template

Click on the "Use this template" button at the top, name your app repo, and GitHub will create a fork of this app to
your account.

> ![use-template.png](./assets/use-template.png)

You can clone the forked app repo and follow the steps below to install the app.

```
git clone https://github.com/YOUR-USERNAME/lightning-template-research-app.git
cd lightning-template-research-app
pip install -r requirements.txt
pip install -e .
```

Once you have installed the app, you can goto the `lightning-template-research-app` folder and
run `lightning run app app.py --cloud` from terminal.
This will launch the template app in your default browser with tabs containing research paper, blog, Training
logs, and Model Demo.

You should see something like this in your browser:

> ![image](./assets/demo.png)

You can modify the content of this app and customize it to your research.
At the root of this template, you will find [app.py](./app.py) that contains the `ResearchApp` class. This class
provides arguments like a link to a paper, a blog, and whether to launch a Gradio demo. You can read more about what
each of the arguments does in the docstrings.

### Highlights

- Provide the link for paper, blog, or training logger like WandB as an argument, and `ResearchApp` will create a tab
  for each.
- Make a poster for your research by editing the markdown file in the [resources](./resources/poster.md) folder.
- Add interactive model demo with Gradio app, update the gradio component present in the \[research_app (
  ./research_app/components/model_demo.py) folder.
- View a Jupyter Notebook or launch a fully-fledged notebook instance (Sharing a Jupyter Notebook instance can expose
  the cloud instance to security vulnerability.)
- Reorder the tab layout using the `tab_order` argument.

### Example

```python
# update app.py at the root of the repo
import lightning as L

  poster_dir = "resources"
  paper = "https://arxiv.org/pdf/2201.12086.pdf"
  blog = "https://blog.salesforceairesearch.com/blip-bootstrapping-language-image-pretraining/"
  github = "https://github.com/salesforce/BLIP"
  tabs = ["Poster", "Blog", "Model Demo", "Notebook Viewer", "Paper"]

  app = L.LightningApp(
      ResearchApp(
          poster_dir=poster_dir,
          paper=paper,
          blog=blog,
          notebook_path="BLIP/demo.ipynb",
          launch_gradio=True,
          tab_order=tabs,
          launch_jupyter_lab=False,  # don't launch for public app, can expose to security vulnerability
      )
  )

```

## FAQs

1. How to pull from the latest template
   code? [Answer](https://stackoverflow.com/questions/56577184/github-pull-changes-from-a-template-repository)
