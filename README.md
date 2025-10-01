**Combining CIC-IDS2017 Files**

# ============================
# Step 1: Mount Google Drive
# ============================
from google.colab import drive
drive.mount('/content/drive')  # Authorize access

# ============================
# Step 2: Import Libraries
# ============================
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# ============================
# Step 3: Load the Dataset from Google Drive|":"
# ============================
# Update this path to the actual location of your file in Drive
file_path = "/content/drive/My Drive/combined_dataset.csv"

try:
    combined_df = pd.read_csv(file_path)
    print("✅ Dataset loaded successfully!")
except FileNotFoundError:
    print(f"❌ Error: File '{file_path}' not found. Check path or filename.")
    exit()
except Exception as e:
    print(f"❌ Unexpected error: {e}")
    exit()

# ============================
# Step 4: Initial Inspection
# ============================
print("\n=== Dataset Overview ===")
print("First 5 rows:")
display(combined_df.head())  # DataFrame preview

print("\nDataset Shape:", combined_df.shape)
print("\nColumn Names:", combined_df.columns.tolist())

# ============================
# Step 5: Data Quality Checks
# ============================
print("\n=== Data Quality ===")
missing = combined_df.isnull().sum()
if missing.sum() == 0:
    print("No missing values detected.")
else:
    print("Missing Values in Columns:")
    print(missing[missing > 0])

# ============================
# Step 6: Label Analysis
# ============================
label_col = None
for col in combined_df.columns:
    if col.strip().lower() == 'label':  # Handles 'Label', 'label', ' Label'
        label_col = col
        break

if label_col:
    print("\n=== Label Distribution ===")
    label_counts = combined_df[label_col].value_counts()
    print(label_counts)

    # Visualization
    plt.figure(figsize=(10, 5))
    sns.barplot(x=label_counts.index, y=label_counts.values)
    plt.title("Class Distribution")
    plt.xticks(rotation=45)
    plt.show()
else:
    print("\n❌ Error: No 'Label' column found. Available columns:", combined_df.columns.tolist())
