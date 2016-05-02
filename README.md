# spring16_Ratings
# OVERVIEW
Many e-commerce websites don’t collect user ratings, or do not provide this data to our website. Hence, it is difficult to determine whether to display the product or not. Simply removing all items without ratings could lead to high opportunity costs, hence, another solution is required. Websites of Electronic gadgets listings decide if they want to pick a particular listing from an e-commerce website and display on their own website. Selection of the right items to list is essential to customers selecting products for purchase, therefore leading to higher revenues.  In this research paper we predict the High - Low rating for any new electronic gadget listing to be introduced on the aggregator website monitored by bargain. The same model can also be used to predict the High - Low Rating on websites that do not support the feature of Average Rating.
# Introduction:
Increase the scope of listings that can be incorporated in our aggregator website, by including those things that do not have ratings. This has the potential to enhance their business income by choice of suitable things that are prone to be acquired by customers, and also avoids the opportunity cost of simply not listing such products. Predict the High - Low Rating for any new electronic gadget listing to be introduced on the aggregator website monitored by our website. The same model can likewise be utilizing to predict the High - Low Rating on websites that do not bolster the elements of Average Rating. 
# Data:
Data is being collected online from the website with details about the electronic gadgets listed on the ecommerce websites. The data collected for prediction is based on the product brand, color, free shipping, average rating of the product, no. of users who rated the product, price of the product, name of the site from which the product has been sold and category of the product.
# Preparation of data:
The data used for performing the model are brand, average rating of the product, shipping time period of the product, name of the site where the product is available and the category of the product. Average rating of the product has created binned variables. The values whose variables are less than two are low rated products and the values whose variables are higher than two are high rated products. Shipping period of the product has been created by missing values which are generated by using Knn predictions from available data using website names, availability of the product, category and shipping of product.
# Methodology:
Given the business objective we set out to achieve, the constraints imposed by this data set were primarily concerned with missing data (missing ratings for almost 500 of the 800 odd records). Moreover, out of these 500 records for which we had the ratings data, shipping period data was missing for over 260 records. We worked our way around the problem by predicting the shipping period values using the KNN method, the amount of data available was still a constraint. First we built a Naïve rule as a benchmark. This was a simple model wherein we predicted the rating based on majority. All records were of the “High” variety, all new records were deemed to be of the same category. The percentage error in this case is around 10.25% which is the benchmark for all other models to beat. In the second step, we selected the Logistical regression model in order to predict the rating of new products. The overbearing rationale behind this was the data intensive nature of K-NN.  
In addition, we have also tried the Naïve Bayes model due to the small size of the training set and with the knowledge that with a smaller training set, we should prefer a high bias and low variance approach like Naïve bayes, I order to compensate for over fitting seen in logistical regression. Although, Naïve Bayes provides biased probabilities while working with categories but we can compare the accuracy of naïve bayes results with our logistic regression model results.   
# Evaluation:
Let’s first assess the benchmark Naïve model. This is a fairly straightforward model wherein the Prediction is based on majority and the error rates are around 10.25%  . Moving to the logistic regression we assess the confusion matrix, as our aim is only prediction and not ranking. Based on this requirement and a base probability cutoff of 0.6, the errors fall dramatically from 10% to 2.2%. Thought the percentage for LOW variety is still high, the same can be ascribed to the fact that we have kept a higher threshold for High variety to get better accuracy there for business reasons.
Next we also evaluate the Naïve Bayes model and compare the error with that of logistic regression. The total error in this case is around 3.69% which is comparable to the logistical regression and beats Naïve rule but logistic regression still better in predicting a high rated product. This can be interpreted as a fact that the fitting which was done in the logistical model was not over fitted to a great extent.  
# Conclusion:
Taking into account the demonstrating exercise completed, we could derive certain proposals for the client of this model and a few learning's which we might want to report.
# Overall Project:
As many e-commerce websites don’t collect user ratings. Hence, it is difficult to determine whether to display the product or not. Simply removing all items without ratings could lead to high opportunity costs, hence, another solution is required. Websites of Electronic gadgets listings decide if they want to pick a particular listing from an e-commerce website and display on their own website. Selection of the right items to list is essential to customers selecting products for purchase, therefore leading to higher revenues. In this project we predict the High - Low rating for any new electronic gadget listing to be introduced on the aggregator website monitored by bargain. The same model can also be used to predict the High - Low Rating on websites that do not support the feature of Average Rating. We find this topic interesting as we even might get more knowledge on how the rating websites work. We collected the data by using few reference which we found online. The references used for the data are http://www.consumerreports.org/cro/electronics-computers/phones- mobile-devices/cell- phones-services/smart-phone- ratings/ratings-overview.htm,
http://www.alibaba.com/showroom/smart-electronic-gadgets.html and http://www.engadget.com/reviews/. These links helped us to go further in our project. The business objective we set out to achieve, the constraints imposed by this data set were primarily concerned with missing data (missing ratings for almost 500 of the 800 odd records). Moreover, out of these 500 records for which we had the ratings data, shipping period data was missing for over 260 records. We worked our way around the problem by predicting the shipping period values using the KNN method, the amount of data available was still a constraint. 
 First we built a Naïve rule as a benchmark. This was a simple model wherein we predicted the rating based on majority. All records were of the “High” variety, all new records were deemed to be of the same category. The percentage error in this case is around 10.25% which is the benchmark for all other models to beat. In the second step, we selected the Logistical regression model in order to predict the rating of new products. The overbearing rationale behind this was the data intensive nature of K-NN.  
In addition, we have also tried the Naïve Bayes model due to the small size of the training set and with the knowledge that with a smaller training set, we should prefer a high bias and low variance approach like Naïve bayes. 
# Code:
import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
import java.util.Scanner;
import java.io.*;
public class Mining {
public static void main(String[] args) {
Map<String,Double> map = new HashMap<String,Double>();
map.put("canon", 0);
map.put("fujifilm", 0);
map.put("lemon", 0);
map.put("nikon", 1.686);
map.put("olympus",0.553);
map.put("zen", 0.458);
map.put("videocon", 0.352);
map.put("sony ericson",2.2345);
map.put("sony", 2.46);
map.put("xolo", 3);
map.put("iball", 3.345134);
map.put("samsung", 4.56);
map.put("apple",5.6789);
map.put("asus", 1.467);
map.put("acer", 0.968);
map.put("intel", 0.34678);
map.put("dell", 1.456);
map.put("lenovo", 3.54);
map.put("lg", 2.765);
Scanner scanner = new Scanner(System.in);
System.out.println("Please Enter the terms ");
String value=scanner.nextLine();
String[] splitValue = value.split(" ");
List<String> splitList1 = new ArrayList<String>(Arrays.asList(splitValue));
List<Double> compareValue = new ArrayList<Double>();
for(String val:splitList1){
for(Map.Entry<String, Double> mapValues:map.entrySet()){
if(mapValues.getKey().equalsIgnoreCase(val)){
compareValue.add(mapValues.getValue());
}
}
}
System.out.println(compareValue);
List<Double> productValues = new ArrayList<Double>();
for(int x=0;x<compareValue.size();x++){
for(int i=0;i<sv1.length;i++){
if(x==i){
Double mVal = compareValue.get(x)*sv1[i];
productValues.add(mVal);
}
}
}
Double squaredVal1 = Math.sqrt(sv1[0])+Math.sqrt(sv1[1])+Math.sqrt(sv1[2])+Math.sqrt(sv1[3])+Math.sqrt(sv1[4]);
Double squaredVal2 = Math.sqrt(sv2[0])+Math.sqrt(sv2[1])+Math.sqrt(sv2[2])+Math.sqrt(sv2[3])+Math.sqrt(sv2[4]);
Double squaredVal3 = Math.sqrt(sv3[0])+Math.sqrt(sv3[1])+Math.sqrt(sv3[2])+Math.sqrt(sv3[3])+Math.sqrt(sv3[4]);
Double squaredVal4 = Math.sqrt(sv4[0])+Math.sqrt(sv4[1])+Math.sqrt(sv4[2])+Math.sqrt(sv4[3])+Math.sqrt(sv4[4]);
Double squaredVal5 = Math.sqrt(sv5[0])+Math.sqrt(sv5[1])+Math.sqrt(sv5[2])+Math.sqrt(sv5[3])+Math.sqrt(sv5[4]);
Double squaredVal6 = Math.sqrt(gv1[0])+Math.sqrt(gv1[1])+Math.sqrt(gv1[2])+Math.sqrt(gv1[3])+Math.sqrt(gv1[4]);
Double squaredVal7 = Math.sqrt(gv2[0])+Math.sqrt(gv2[1])+Math.sqrt(gv2[2])+Math.sqrt(gv2[3])+Math.sqrt(gv2[4]);
Double squaredVal8 = Math.sqrt(gv3[0])+Math.sqrt(gv3[1])+Math.sqrt(gv3[2])+Math.sqrt(gv3[3])+Math.sqrt(gv3[4]);
Double squaredVal9 = Math.sqrt(gv4[0])+Math.sqrt(gv4[1])+Math.sqrt(gv4[2])+Math.sqrt(gv4[3])+Math.sqrt(gv4[4]);
Double squaredVal10 = Math.sqrt(gv5[0])+Math.sqrt(gv5[1])+Math.sqrt(gv5[2])+Math.sqrt(gv5[3])+Math.sqrt(gv5[4]);
//Double inputSquareVal = Math.sqrt(sv1[0])+Math.sqrt(sv1[1])+Math.sqrt(sv1[2])+Math.sqrt(sv1[3])+Math.sqrt(sv1[4])+Math.sqrt(sv1[5])+Math.sqrt(sv1[6]);
//Map<String, Double> compareValue;
Double cSquR = Math.sqrt(compareValue.get(0))+Math.sqrt(compareValue.get(1))+Math.sqrt(compareValue.get(2))+Math.sqrt(compareValue.get(3))+Math.sqrt(compareValue.get(4))+Math.sqrt(compareValue.get(5))+Math.sqrt(compareValue.get(6));
Double iMul = productValues.get(0)+productValues.get(1)+productValues.get(2)+productValues.get(3)+productValues.get(4);
Float cosine1 = (float) (iMul/(squaredVal1*cSquR));
Float cosine2 = (float) (iMul/(squaredVal2*cSquR));
Float cosine3 = (float) (iMul/(squaredVal3*cSquR));
Float cosine4 = (float) (iMul/(squaredVal4*cSquR));
Float cosine5 = (float) (iMul/(squaredVal5*cSquR));
Float cosine6 = (float) (iMul/(squaredVal6*cSquR));
Float cosine7 = (float) (iMul/(squaredVal7*cSquR));
Float cosine8 = (float) (iMul/(squaredVal8*cSquR));
Float cosine9 = (float) (iMul/(squaredVal9*cSquR));
Float cosine10 = (float) (iMul/(squaredVal10*cSquR));
System.out.println("Cosine Values: "+cosine1+" "+cosine2+" "+cosine3+" "+cosine4+" "+cosine5+" "+cosine6+" "+cosine7+" "+cosine8+" "+cosine9+" "+cosine10);
List<Float> list = new ArrayList<Float>();
list.add(cosine1);
list.add(cosine2);
list.add(cosine3);
list.add(cosine4);
list.add(cosine5);
list.add(cosine6);
list.add(cosine7);
list.add(cosine8);
list.add(cosine9);
list.add(cosine10);
int x = 0;
int y = 0;
for(Float val : list){
if(val<=0.3){
x = x+1;
}else{
y=y+1;
}
}
if(x<y){
System.out.println("low");
}else{
System.out.println("high");
}
}

}
# Project Management:

Team member	Roles and skills
Ruthvik Reddy Gidde	Working on Weka
Chandra Charan Saineni	data analysis and documentation
Jyothsna Sappid	data analysis and implementation

The Team was of Three and the work was distributed among where Rutvik Reddy Gidde worked with Weka and Chandra Charan Rao Saineni worked with the Data analysis and documentation and Jyothsna Sappidi worked on the Data analysis and implementation part. The work distributed was even and all the three had to good tasks to accomplish to meet the project goals. The project deliverables were clearly stated.
# Outcomes:
The Data mining outcome was a success. The data used for performing the model are brand, average rating of the product, shipping time period of the product, name of the site where the product is available and the category of the product. Average rating of the product has created binned variables. The values whose variables are less than two are low rated products and the values whose variables are higher than two are high rated products. The project checkpoints that were established helped us a lot for completing the project. 
