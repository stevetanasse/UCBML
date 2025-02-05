# Objective
Determine the primary characteristics that impact the price of a used car. This information will be used by an used car dealership to fine-tune their inventory.

UsedCars.ipynb

To focus the use case for the model, the following assumptions are made about the assignment:

The used car dealership is in the business of buying and selling standard automobiles to consumers. For example, the dealership will not be selling commercial vehicles like 18-wheeler semi trucks or other specialty vehicles like busses, military vehicles, motorcycles, RVs, etc. Nor will the dealerships be selling junked or salvaged vehicles, nor cars $500 or less. Additionally, they will not be selling specialty cars that exceed $150,000.

The used car dealership will be selling only automobiles manufactured after 1990, since vehicles older than that will likely either be specialty vehicles and the dataset has less information for these types of vehicles.

The used car dealership will not buy or sell cars where the odometer reports 200,000 or more miles.

The price value in the dataset is understood to be the price at which the vehicle was sold.

# Conclusion
The dataset does not provide enough meaningful information to identify vehicle features that customers find valuable. The mean absolute error for predicting price for the highest performing model is $4534.84. With the mean vehicle value of $20105.75, the error is almost a quarter of the price of the average vehicle. Therefore the model is not reliable for predicting the price of vehicles nor for inferring the vehicle characteristics that interest customers. Even though the model is flawed, the model does report the 'brand_value' as the important feature in determining the price of the vehicle with a 0.81 correlation to the price. The 'age' features has a -0.56 correlation followed by 'odometer' with a -0.54 correlation.

Model creation wasn't successful because the provided dataset does not contain meaningful feature information that customer typically look for in a vehicle. For example, features like gas mileage, passenger capacity, luggage space, air conditioning, etc. were absent from the dataset.

If the client would like to create a machine learning model that can predict the price of vehicles and infer the characteristics that customers value in a car, then more detailed vehicle and customer information is required. Vehicle information is just one side of a transaction. Customer information would be helpful in matching customer and regional demographics to vehicle preferences.

One approach with the current dataset is to leverage the VIN to obtain more objective information about the vehicle. This would require making API calls to online resources like nhtsa.gov. However, the VIN would not reveal all vehicle amenities. Additional research into specific manufacturers and models would be necessary to obtain a detailed list of amenities.
