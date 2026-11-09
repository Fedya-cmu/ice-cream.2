# Ice Cream Sales Predictor (version 2: temperature, rain chance and weekend)

Pick a city and a date. The app asks a free weather API for the forecast high and the chance of
rain, checks whether the date is a weekend, gives all three to a trained model, and shows the
predicted number of cones sold, with a short business message.

## Files
- `app.py`: the Streamlit app
- `model.pkl`: the trained model (a linear regression with 3 predictors), saved from the notebook
- `train_model.ipynb`: the notebook that makes the data, trains the model and saves `model.pkl`
- `requirements.txt`: the packages Streamlit Cloud installs for you

## How it works
1. The user picks a city and a date.
2. The app asks Open-Meteo (free, no key, no sign-up) for the forecast high for that day.
3. The app works out whether the date is a weekend (Saturday or Sunday).
4. The model predicts sales from `temperature`, `rain_chance` and `weekend`, in the same
   column order as in training.
5. The app shows the number, a warning if the temperature is outside what the model learned
   from, and a short message.

## What changed from version 1
Two new predictors: the chance of rain (people buy fewer cones on wet days) and weekend
(more foot traffic). The model was retrained in `train_model.ipynb` and saved again as `model.pkl`.

The model was trained on made-up data, to show the steps. The effects of rain and weekends are
assumptions, not findings from a real shop. Replace it with a model trained on
real data to use this for a real business.

## Run it online for free (no terminal)
1. Put `app.py`, `model.pkl` and `requirements.txt` (and optionally the notebook and README) in a public GitHub repository (upload them in the browser).
2. On share.streamlit.io, create an app from the repository, main file `app.py`.
No API key is needed.

## If something goes wrong
- An error when loading `model.pkl`: check that the file is in the repository next to `app.py`,
  and that `scikit-learn` is listed in `requirements.txt`.
- An error about the forecast: the weather service may be busy. Wait a minute and try again.
