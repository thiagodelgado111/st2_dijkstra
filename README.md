
LEVAETRAZ
=======================

- RabbitMQ ou DelayedJob para processamento em background
- MongoDB pra armazenar os mapas
- Algoritmo genético para TSP?
- Sinatra


# Parâmetros de entrada (JSON)

## Malha logística

```json
{
	"name" : "Mapa SP",
	"points" : [
		{
			"departure": "A", 
			"destination": "B",
			"distanceInKilometer": 10 
		},
		{
			"departure": "B",
			"destination": "D",
			"distanceInKilometer": 15 
		},
		{
			"departure": "A",
			"destination": "C",
			"distanceInKilometer": 20 
		},
		{
			"departure": "C",
			"destination": "D",
			"distanceInKilometer": 30 
		},
		{
			"departure": "B",
			"destination": "E",
			"distanceInKilometer": 50 
		},
		{
			"departure": "D",
			"destination": "E",
			"distanceInKilometer": 30 
		}
	]
}
```

## Menor valor de entrega e melhor caminho (TSP)

- Parâmetros de entrada para se calcular qual é a melhor rota
  * Malha logística
  * Nome do ponto de origem da jornada
  * Nome do ponto de destino final da jornada
  * Autonomia do caminhão (Km/L)
  * $ Valor do litro de combustível


  Exemplo de entrada: 
 
```json
{
	"map" : 
	{
		"name" : "Mapa SP",
		"points" : [
			{
				"departure": "A", 
				"destination": "B",
				"distanceInKilometer": 10 
			},
			{
				"departure": "B",
				"destination": "D",
				"distanceInKilometer": 15 
			},
			{
				"departure": "A",
				"destination": "C",
				"distanceInKilometer": 20 
			},
			{
				"departure": "C",
				"destination": "D",
				"distanceInKilometer": 30 
			},
			{
				"departure": "B",
				"destination": "E",
				"distanceInKilometer": 50 
			},
			{
				"departure": "D",
				"destination": "E",
				"distanceInKilometer": 30 
			}
		]
	},
	"fuelCostPerLiter" : 2.5,
	"vehicleAutonomyPerKilometer": 10,
	"origin" : "A",
	"destination": "D"
}
```

- Minimizar gasto levando em consideração a distância euclidiana entre os pontos:
  * min(cost) = (sum(distanceP2P) / vehicleAutonomy) * costPerLiter