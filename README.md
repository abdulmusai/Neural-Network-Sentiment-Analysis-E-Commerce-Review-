# Neural-Network-Sentiment-Analysis-E-Commerce-Review-
This will analyze customer review data using Python, TensorFlow/Keras, and natural language processing techniques to build a deep learning sentiment classifier. It will also standardize text data, implement TextVectorization and embedding architectures, train a binary neural network, and translate prediction confidence.
# Neural Network Sentiment Analysis – E-Commerce Reviews

## Strategic Discovery-to-Action (DTA) Report

### 1. Discovery Phase: Data Refinement & Text Pipeline
- **Missing Value & Target Strategy**: Empty review strings were safely converted to generic placeholders. To prevent blurred mathematical signals, all neutral 3-star reviews were completely omitted from the workspace. Ratings of 4 and 5 were encoded as `1` (Positive), while ratings of 1 and 2 were encoded as `0` (Negative).
- **Text Standardization & Rationale**: Raw text features vary wildly in punctuation, capitalization, and grammar. We utilized Keras `TextVectorization` configured with a maximum vocabulary restriction of `10,000` tokens. The layer standardizes arrays by forcing lowercase transitions and completely removing punctuation arrays before mapping individual words to sequential integer keys.

### 2. Technical Phase: Architecture & Modeling Choices

The architecture consists of a highly scalable, dense embedding layout:
- **Embedding Layer**: Translates sparse, high-dimensional word index tokens into dense, continuous vectors of size 16, allowing semantic word relationships to cluster together geometrically.
- **GlobalAveragePooling1D**: Averages the sequence vectors across the entire review length. This acts as a powerful dimensional compressor, removing length-variance noise and allowing standard dense layers to read the output seamlessly.
- **Hidden & Output Configuration**: A 16-node `ReLU` layer handles deep feature processing, feeding directly into a single `Sigmoid` node that outputs an exact continuous probability scale ranging strictly between `0.0` (Absolute Negativity) and `1.0` (Absolute Positivity).

### 3. Action Phase: Business Workflow & Threshold Rationale
When evaluated against the mandatory validation string, **"The product arrived broken and I am very unhappy"**, the model yields a probability score approaching **0.00**, accurately registering extreme negative consumer intent.

#### Automated Escalation Workflow Design
To maximize operational efficiency without over-burdening human support teams, the following automated operational routing matrix is established:
