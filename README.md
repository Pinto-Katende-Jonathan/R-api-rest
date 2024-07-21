# R-api-rest
R api rest for machine learning model

1. **Entraîner et exporter le modèle avec R**
- Entraîner et exporter le modèle avec REntraînez votre modèle de machine learning en R.
- Sauvegardez le modèle en utilisant des outils comme saveRDS().
```R
saveRDS(model, file = "model.rds")
```

2. **Créer une API RESTful avec R
- Utilisez un framework comme Plumber pour créer une API RESTful qui hébergera votre modèle.**
```R
library(plumber)

# Load your model
model <- readRDS("model.rds")

# Create a function to predict
#* @post /predict
predict_function <- function(input_data){
  # Preprocess input_data as needed
  prediction <- predict(model, input_data)
  return(list(prediction = prediction))
}

# Create the plumber router
r <- plumb()
r$handle("POST", "/predict", predict_function)
r$run(host = "0.0.0.0", port = 8000)
```
Déployez cette API sur un serveur accessible par votre application mobile.
