Toddler Nutrition Monitoring App
Project Description
The Toddler Nutrition Monitoring App is an AI-powered solution designed to combat stunting in Indonesia by enabling parents and community health workers (kader posyandu) to monitor the nutritional intake of children under five. Leveraging the IBM Granite Vision 3.2-2B model, the app analyzes photos of toddler meals to identify food types, estimate nutritional content (calories, protein, vitamins), and provide tailored recommendations to improve dietary balance. Built with a focus on Indonesia’s unique dietary and cultural context, it supports local languages, offline functionality, and aligns with national nutrition guidelines such as Isi Piringku.
Key Objectives

Prevent Stunting: Facilitate early detection of nutritional deficiencies to reduce Indonesia’s stunting rate (currently ~21.6% as of 2023).
Empower Communities: Equip posyandu workers with an accessible tool to monitor toddler nutrition efficiently.
Enhance Accessibility: Provide offline capabilities and local language support for rural areas with limited connectivity.
Promote Education: Increase parental awareness of balanced diets using affordable, locally available foods.

Why IBM Granite Vision?
The app utilizes the IBM Granite Vision 3.2-2B model, a state-of-the-art vision-language model optimized for image analysis and text generation. Its key strengths include:

Accurate Image Recognition: Capable of identifying diverse Indonesian foods (e.g., nasi uduk, sayur bayam, ikan asin) with high precision when fine-tuned on local datasets.
Natural Language Output: Generates clear, context-aware nutritional reports and recommendations in Bahasa Indonesia or local languages.
Efficient Processing: Suitable for deployment on both cloud and edge devices, enabling offline functionality in resource-constrained environments.

Features

Food Image Analysis:
Upload a photo of a toddler’s meal (PNG/JPEG) via a command-line interface or future mobile app.
IBM Granite Vision identifies food types and estimates nutritional content using a localized Indonesian food database.


Nutritional Reports:
Provides detailed reports on calories, protein, and vitamins in Bahasa Indonesia or local languages (e.g., Javanese, Sundanese).
Example output: “Meal contains 250 kcal, 8g protein, sufficient iron, but low in vitamin A.”


Personalized Recommendations:
Suggests practical dietary improvements, e.g., “Add carrots or papaya to boost vitamin A,” aligned with Isi Piringku guidelines.


Weekly Monitoring:
Tracks nutritional intake over time and saves data to a CSV report (weekly_nutrition_report.csv).
Detects patterns like chronic protein deficiency to flag potential stunting risks.


Accessibility:
Supports offline mode for rural areas with limited internet.
Designed for low-tech literacy users, with plans for a user-friendly mobile interface.


Educational Module:
Includes a chatbot (powered by Granite Vision) to answer questions like “What foods are good for a 2-year-old?”
Promotes affordable, local foods (e.g., tempe, kangkung, bananas).



Installation
Prerequisites

Python 3.8+
Dependencies: replicate, pandas, Pillow
Replicate API token (obtain from Replicate)
Optional: Local dataset of Indonesian food images for fine-tuning

Setup Instructions

Clone the Repository:git clone https://github.com/username/toddler-nutrition-monitor.git
cd toddler-nutrition-monitor


Install Dependencies:pip install -r requirements.txt

The requirements.txt includes:replicate
pandas
Pillow


Set Environment Variable:Set your Replicate API token:export REPLICATE_API_TOKEN=your_api_token_here

On Windows, use:set REPLICATE_API_TOKEN=your_api_token_here


Verify Setup:Ensure Python and dependencies are installed correctly:python -m pip show replicate pandas Pillow



Usage

Prepare a Food Image:
Use a PNG or JPEG image of a toddler’s meal (e.g., rice, spinach, fish).
Place the image in the project directory or note its file path.


Run the Script:python nutrition_monitor.py


Enter Image Path:When prompted, provide the path to the food image:Enter the path to the food image (PNG/JPEG): ./data/nasi_bayam.jpg


Review Output:The app will:
Analyze the image using IBM Granite Vision.
Display detected foods, nutritional estimates, and recommendations.
Save results to weekly_nutrition_report.csv.
Assess stunting risk based on weekly data.Example output:

Detected Foods: nasi, sayur bayam, ikan
Total Calories: 359 kcal
Total Protein: 27.6 g
Vitamins: B1, A, C, D
Recommendations: Add carrots or papaya to boost vitamin A.
Report saved to: weekly_nutrition_report.csv
Stunting Risk Analysis:
- No stunting risk detected based on weekly data.



Dataset
The current implementation uses a simplified nutrition database (nutrition_db) with common Indonesian foods. For production use, we recommend:

Local Dataset: Collect 10,000+ images of Indonesian meals (e.g., nasi uduk, gado-gado, ikan asin) from diverse regions.
Annotation: Label images with nutritional data from the Tabel Komposisi Pangan Indonesia.
Fine-Tuning: Train IBM Granite Vision on this dataset for improved accuracy.

Interested in contributing a dataset? See the Contributing section.
Technical Details

Model: IBM Granite Vision 3.2-2B (via Replicate API)
Input: PNG/JPEG images of toddler meals
Output: Nutritional analysis, recommendations, and stunting risk assessment
Backend: Python with Replicate, Pandas, and Pillow
Database: Local dictionary (extendable to integrate with Tabel Komposisi Pangan Indonesia)
Security: Image and report data are processed locally; API calls use encrypted HTTPS.
Offline Support: Planned for edge deployment using optimized models (e.g., TensorFlow Lite).

Challenges and Future Enhancements
Challenges

Dataset Limitations: Limited coverage of diverse Indonesian foods.
Solution: Crowdsourcing via posyandu workers and partnerships with universities.


Nutrition Estimation: Portion size variability affects accuracy.
Solution: Integrate portion estimation algorithms and national food composition tables.


Connectivity: Rural areas often lack internet access.
Solution: Optimize for edge computing and offline mode.


User Literacy: Low tech literacy among rural users.
Solution: Develop a mobile app with intuitive UI and voice guidance.



Planned Enhancements

Mobile app with a graphical interface (using Flask or Streamlit).
Integration with anthropometric data (weight, height) for comprehensive stunting assessment.
Support for additional local languages (e.g., Balinese, Minang).
Collaboration with Indonesia’s Ministry of Health for nationwide rollout.

Contributing
We welcome contributions to improve the app, including:

Expanding the food dataset with regional Indonesian dishes.
Enhancing model accuracy through fine-tuning.
Adding support for more local languages.
Developing unit tests or UI improvements.

To contribute:

Fork the repository.
Create a feature branch: git checkout -b feature/your-feature.
Commit changes: git commit -m "Add your feature".
Push to the branch: git push origin feature/your-feature.
Open a pull request with a detailed description.


