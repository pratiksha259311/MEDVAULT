# MEDVAULT
AI-driven health records for rural areas with offline-first access, SMS-based retrieval, mental health insights, cost-effective treatment suggestions . Ensures secure, AI-powered healthcare anywhere—bridging gaps &amp; saving lives. 
import pandas as pd
import matplotlib.pyplot as plt

# Create the dataset
data = {
    'Country': ['Country A', 'Country B', 'Country C', 'Country D', 'Country E'],
    'Remote Area Population': [500000, 750000, 600000, 800000, 1000000],
    'Healthcare Facilities': [20, 15, 10, 25, 30],
    'Internet Connectivity Level': ['Low', 'Very Low', 'Medium', 'Low', 'Very Low'],
    'Percentage of Population with Access to Healthcare': [35, 25, 40, 45, 30],
    'Possible Recovery Rate with AI and Interconnected Hospitals': [75, 70, 80, 85, 72],
    'Possible Recovery Rate with MedVault AI': [85, 80, 90, 92, 82]
}

# Convert the dictionary to a DataFrame
df = pd.DataFrame(data)

# Calculate percentage improvement with MedVault AI
df['Improvement (%)'] = ((df['Possible Recovery Rate with MedVault AI'] - 
                          df['Possible Recovery Rate with AI and Interconnected Hospitals']) / 
                          df['Possible Recovery Rate with AI and Interconnected Hospitals']) * 100

# Sort data by MedVault AI recovery rate for better visualization
df = df.sort_values(by='Possible Recovery Rate with MedVault AI', ascending=True)

# Plot the data
plt.figure(figsize=(10, 6))
plt.plot(df['Country'], df['Possible Recovery Rate with AI and Interconnected Hospitals'], 
         label='Recovery Rate with AI & Interconnected Hospitals', marker='o', linestyle='-', color='royalblue')
plt.plot(df['Country'], df['Possible Recovery Rate with MedVault AI'], 
         label='Recovery Rate with MedVault AI', marker='o', linestyle='-', color='gold')

# Add data labels for better readability
for i, txt in enumerate(df['Possible Recovery Rate with AI and Interconnected Hospitals']):
    plt.text(i, txt + 1, f"{txt}%", ha='center', fontsize=10, color='royalblue')

for i, txt in enumerate(df['Possible Recovery Rate with MedVault AI']):
    plt.text(i, txt + 1, f"{txt}%", ha='center', fontsize=10, color='gold')

plt.xlabel('Country')
plt.ylabel('Possible Recovery Rate (%)')
plt.title('Possible Recovery Rates in Remote Areas')
plt.legend()
plt.grid(True)
plt.show()

# Display the dataset with improvements
print("Healthcare Facilities in Remote Areas with MedVault AI Impact")
print(df[['Country', 'Possible Recovery Rate with AI and Interconnected Hospitals', 
          'Possible Recovery Rate with MedVault AI', 'Improvement (%)']])
