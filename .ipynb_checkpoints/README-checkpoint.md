# clip-vs-human-annotations
# **Comparing CLIP Classification to Human Data Annotation**

## **Overview**
This project evaluates how well OpenAI's **CLIP** model classifies potentially inappropriate content compared to human annotators. By analyzing a small curated dataset of Instagram-like images, we assess **CLIP's strengths and weaknesses** in identifying content that may be unsuitable for children.

## **Project Goals**
- Compare **human annotations** with **CLIP-generated classifications**.
- Examine **accuracy and consistency** across different content categories.
- Highlight **challenges and limitations** of using CLIP for unsupervised moderation.
- Explore the potential for **scaling annotation workflows** with AI assistance.

## **Dataset & Categories**
We annotated a small set of images based on the following dimensions:
- **Attire** – Does the image contain revealing or inappropriate clothing?
- **Sexual Content** – Is there suggestive body language or explicit content?
- **Substances** – Are alcohol, cigarettes, or drugs present?
- **Gestures** – Are there offensive gestures or symbols?
- **Violence** – Does the image depict weapons, fighting, or aggression?
- **Gore** – Is there blood, injuries, or disturbing content?
- **Overall** – A general classification of whether the image is **appropriate, questionable, or inappropriate**.

## **Methodology**
1. **Human Annotation** – Images were manually reviewed and rated on a three-point scale (**no violation, minor violation, major violation**).
2. **CLIP Classification** – The CLIP model was prompted with descriptive labels and returned probability scores for each category.
3. **Comparison** – A **difference table** was generated to quantify where CLIP disagreed with human labels.

## **Key Findings**
- **CLIP performs well on some categories (e.g., Attire, Gore) but struggles with nuance** in areas like Sexual Content and Gestures.
- **Raw probability scores can be misleading**, requiring careful threshold tuning.
- **A single inappropriate misclassification can have major consequences**, making unsupervised CLIP moderation unsuitable for child-safe spaces.
- **Models like CLIP could potentially be used as an initial filter**, reducing manual workloads. 
- **Human annotation remains essential** to account for cultural, contextual, and evolving definitions of "inappropriate."

## **Installation & Usage**
### **1. Clone the Repository**
```bash
git clone https://github.com/rhummel2323/clip-vs-human-annotations.git
cd clip-vs-human-annotations
```
### **2. Install Dependencies**
```bash
conda install python==3.12.9
conda install pytorch torchvision cudatoolkit
conda install pip
pip install ftfy regex tqdm
pip install git+https://github.com/openai/CLIP.git
pip install numpy pandas matplotlib jupyter
```
### **3. Run the Analysis**
Execute the main Jupyter notebook:
```bash
jupyter notebook
```

## **Results**
The table below shows the **number of mismatched dimensions** per image and whether CLIP's overall classification matched human annotation.

| Image  | Dimensions Mismatched | Overall Match |
|--------|----------------------|--------------|
| post1  | 1                    | ❌ False    |
| post2  | 1                    | ✅ True     |
| post3  | 2                    | ✅ True     |
| post4  | 2                    | ❌ False    |
| post5  | 2                    | ✅ True     |
| post6  | 1                    | ❌ False    |
| post7  | 0                    | ✅ True     |
| post8  | 1                    | ✅ True     |

## **Limitations & Future Work**
- **Dataset Size** – A small sample size limits broader conclusions.
- **Prompt Optimization** – CLIP results **vary significantly** based on prompt wording.
- **Unsupervised Use Cases** – The model **should not be deployed** without human oversight.

## **License**
This project is licensed under the **MIT License** – see [LICENSE](LICENSE) for details.

## **Contributing**
Contributions are welcome! Feel free to open an issue or submit a pull request.

