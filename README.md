# enhanced_healthcare_diagnosis.py 
def diagnose(symptoms): 
    symptoms = set([s.lower().strip() for s in symptoms]) 
    # Predefined conditions with symptom sets 
    conditions = { 
        "Flu": {"fever", "cough", "headache", "body pain"}, 
        "Common Cold": {"cold", "sneezing", "sore throat"}, 
        "COVID-19": {"fever", "dry cough", "loss of taste", "loss of smell"}, 
        "Migraine": {"headache", "nausea", "sensitivity to light"}, 
        "Stomach Infection": {"stomach pain", "diarrhea", "vomiting"}, 
        "Urinary Tract Infection (UTI)": {"burning urination", "frequent urination", "lower abdominal 
pain"}, 
        "Allergy": {"sneezing", "itchy eyes", "runny nose"}, 
        "Asthma": {"shortness of breath", "chest tightness", "wheezing"}, 
        "Dehydration": {"dry mouth", "fatigue", "dizziness"}, 
    } 
    for condition, condition_symptoms in conditions.items(): 
        if symptoms & condition_symptoms == condition_symptoms: 
            return condition, get_treatment(condition) 
    if "chest pain" in symptoms: 
        return "Possible Heart Issue", "Seek immediate medical attention." 
    return "Unknown Condition", "Symptoms do not match any known condition in the database. 
Please consult a doctor." 
def get_treatment(condition): 
    treatments = { 
        "Flu": "Take rest, stay hydrated, and use paracetamol if needed. Consult a doctor if symptoms 
persist.", 
        "Common Cold": "Drink warm fluids, rest, and use over-the-counter cold medicine.", 
        "COVID-19": "Isolate yourself, stay hydrated, and monitor oxygen levels. Seek medical help if 
breathing difficulty occurs.", 
        "Migraine": "Avoid bright lights, rest in a dark room, and use prescribed migraine medication.", 
        "Stomach Infection": "Drink ORS, avoid solid food temporarily, and consult a doctor if diarrhea 
continues.", 
        "Urinary Tract Infection (UTI)": "Drink plenty of water and consult a doctor for antibiotics.", 
        "Allergy": "Avoid allergens, use antihistamines, and consult an allergist if needed.", 
        "Asthma": "Use an inhaler if prescribed, avoid dust/pollutants, and visit a doctor for long-term 
management.", 
        "Dehydration": "Drink water, ORS solution, and avoid caffeine or alcohol.", 
    } 
    return treatments.get(condition, "General treatment advice not available.") 
def get_user_details(): 
    print("Welcome to the Healthcare Diagnosis Assistant") 
    name = input("Enter your name: ") 
    age = input("Enter your age: ") 
    return name, age 
def get_symptoms(): 
    print("\nEnter your symptoms separated by commas (e.g., fever, cough, headache):") 
    symptoms_input = input("Symptoms: ") 
    return symptoms_input.split(",")
    def main(): 
    name, age = get_user_details() 
    symptoms = get_symptoms() 
    print("\nDiagnosing your symptoms...") 
    condition, advice = diagnose(symptoms) 
    print(f"\n--- Diagnosis Report ---") 
    print(f"Name: {name}") 
    print(f"Age: {age}") 
    print(f"Condition: {condition}") 
    print(f"Advice: {advice}") 
    print(f"------------------------") 
if __name__ == "__main__": 
    main() 
