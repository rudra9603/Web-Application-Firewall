# Web Application Firewall with Machine Learning

## Project Overview
This project is a **Web Application Firewall (WAF)** powered by **machine learning** to provide real-time protection against malicious web traffic. By analyzing incoming HTTP requests, the WAF classifies them as either **legitimate** or **malicious** and takes appropriate actions, such as blocking harmful requests or forwarding safe ones to the target server.

The system leverages **ensemble machine learning models** and a **proxy server** to ensure robust web security while maintaining low latency. The project achieves a high detection accuracy of **97%** and can identify threats such as **SQL injection**, **cross-site scripting (XSS)**, and other web-based attacks.

---

## Key Features
- **Real-Time Threat Detection:**
  Automatically detects and blocks malicious web traffic in real-time.

- **Ensemble Machine Learning Models:**
  Utilized algorithms like **Logistic Regression**, **Random Forest**, **Gradient Boosting**, **XGBoost**, and others for high-accuracy predictions.

- **Proxy Server Integration:**
  Built a scalable **HTTP proxy server** to intercept, analyze, and classify incoming requests.

- **Custom Feature Engineering:**
  Extracts key features from HTTP request paths and bodies to identify potential attack patterns (e.g., special characters, keywords, lengths).

- **High Precision:**
  Achieved a **99% precision** in malicious request detection, reducing false positives.

- **Seamless Deployment:**
  Fully integrated the machine learning model and feature extractor into the proxy server for real-time performance.

- **Security Tools Compatibility:**
  Data collected using tools like **Burp Suite** and **OWASP ZAP** for vulnerability analysis.

---

## Architecture
1. **Feature Extraction:**
   - Parses HTTP request paths and bodies.
   - Extracts numerical and categorical features such as:
     - Frequency of special characters (e.g., `'`, `"`, `;`, `--`).
     - Presence of malicious keywords (e.g., `SELECT`, `DROP`, `SCRIPT`).
     - Length-based metrics for path and body.

2. **Model Training:**
   - Preprocessed datasets using **scikit-learn**.
   - Trained multiple machine learning algorithms and combined them into an ensemble model.
   - Saved the best-performing model with a **scaler** and **label encoder** for deployment.

3. **Proxy Server Integration:**
   - Intercepts incoming requests via a custom **HTTP server**.
   - Extracts features and scales them for the machine learning model.
   - Blocks malicious requests with **403 Forbidden responses** or forwards legitimate ones to the target server.

---

## Tech Stack
- **Programming Languages:** Python
- **Libraries/Frameworks:**
  - Machine Learning: `scikit-learn`, `XGBoost`
  - Networking: `http.server`, `requests`
- **Tools:** Burp Suite, OWASP ZAP
- **Deployment:** Localhost proxy server

---

## How It Works
1. **Setup the Proxy Server:**
   - Start the proxy server to intercept HTTP traffic on a specified port.

2. **Feature Extraction & Classification:**
   - Extract features from the intercepted HTTP request.
   - Use the pre-trained machine learning model to classify the request as either malicious or legitimate.

3. **Action Based on Prediction:**
   - If malicious, block the request with a `403 Forbidden` response.
   - If legitimate, forward the request to the intended server.

4. **Logging:**
   - Logs all incoming requests and their classification for further analysis.

---

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/web-application-firewall.git
   cd web-application-firewall
   ```
2. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```
3. Start the proxy server:
   ```bash
   python waf_proxy_server.py
   ```
4. Update the base path for the pre-trained models if needed:
   - Modify the `base_path` variable in the script to point to the directory containing the saved models.

---

## Usage
- Start the proxy server on `localhost:8080`:
  ```bash
  python waf_proxy_server.py
  ```
- Configure your browser or application to use the proxy server (e.g., `127.0.0.1:8080`).
- Monitor the logs to see real-time classification of HTTP requests.

---

## Performance
- **Detection Accuracy:** 97%
- **Precision:** 99%
- **Recall:** 96%

---

## Future Enhancements
- Add support for **HTTPS traffic**.
- Extend feature extraction to handle more advanced attack patterns.
- Integrate a **dashboard** for real-time monitoring and analytics.
- Optimize the system for deployment on cloud platforms.

---

## Contributing
Feel free to submit issues or pull requests to improve the project. Contributions are welcome!

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments
- Tools: Burp Suite, OWASP ZAP
- Libraries: scikit-learn, XGBoost
- Dataset: Demo data collected for training and testing.

---

### Contact
For any questions or inquiries, feel free to contact me at **rudra9603m@gmail.com** or connect on [LinkedIn](www.linkedin.com/in/rudra-kumar-a5ba44243).

