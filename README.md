# medical_ner
Name Entity Recognition model that can detect SYMPTOM,DISEASE,DRUG and LAB.
The model is trained on private dataset using SPACY. 
use case.

``` 
import spacy
#Loading the custom model
nlp_ner = spacy.load("model-best")

#Selecting the sample note.

note = """PAST MEDICAL HISTORY:,  Significant for hypertension.  The patient takes hydrochlorothiazide for this.  She also suffers from high cholesterol and takes Crestor. \n She also has dry eyes and uses Restasis for this.  She denies liver disease, kidney disease, cirrhosis, hepatitis, diabetes mellitus, thyroid disease,\n  bleeding disorders, prior DVT, HIV and gout.  She also denies cardiac disease and prior history of cancer.,PAST SURGICAL HISTORY: , \n  Significant for tubal ligation in 1993.  She had a hysterectomy done in 2000 and a gallbladder resection done in 2002.,MEDICATIONS: , Crestor 20 mg p.o. daily, \n  hydrochlorothiazide 20 mg p.o. daily, Veramist spray 27.5 mcg daily, Restasis twice a day and ibuprofen two to three times a day.,ALLERGIES TO MEDICATIONS: , \n  Bactrim which causes a rash.  The patient denies latex allergy.,SOCIAL HISTORY: , The patient is a life long nonsmoker.  She only drinks socially one to two drinks a month.  \n  She is employed as a manager at the New York department of taxation.  She is married with four children.,FAMILY HISTORY: , Significant for type II diabetes on her mother's side as well as liver and heart failure.  \n  She has one sibling that suffers from high cholesterol and high triglycerides.,REVIEW OF SYSTEMS: , Positive for hot flashes.  She also complains about snoring and occasional slight asthma. \n   She does complain about peripheral ankle swelling and heartburn.  She also gives a history of hemorrhoids and bladder infections in the past.  She has weight bearing joint pain as well as low back degenerating discs.  She denies obstructive sleep apnea, kidney stones, bloody bowel movements, ulcerative colitis, Crohn's disease, dark tarry stools and melena.,PHYSICAL EXAMINATION:  ,On examination temperature is 97.7, pulse 84, blood pressure 126/80, respiratory rate was 20.  Well nourished, well developed in no distress.  Eye exam, pupils equal round and reactive to light.  Extraocular motions intact.  Neuro exam deep tendon reflexes 1+ in the lower extremities.  No focal neuro deficits noted.  Neck exam nonpalpable thyroid, midline trachea, no cervical lymphadenopathy, no carotid bruit.  Lung exam clear breath sounds throughout without rhonchi or wheezes however diminished.  Cardiac exam regular rate and rhythm without murmur or bruit.  Abdominal exam positive bowel sounds, soft, nontender, obese, nondistended abdomen.  No palpable tenderness.  No right upper quadrant tenderness.  No organomegaly appreciated.  No obvious hernias noted.  Lower extremity exam +1 edema noted.  Positive dorsalis pedis pulses.,ASSESSMENT: , The patient is a 56-year-old female who presents to the bariatric surgery service with a body mass index of 41 with obesity related comorbidities.  The patient is interested in gastric bypass surgery.  The patient appears to be an excellent candidate and would benefit greatly in the management of her comorbidities.,PLAN: , In preparation for surgery will obtain the usual baseline laboratory values including baseline vitamin levels.  Will proceed with our usual work up with an upper GI series as well as consultations with the dietician and the psychologist preoperatively.  I have recommended six weeks of Medifast for the patient to obtain a 10% preoperative weight loss"""

#Run NER in sample note.
doc = nlp_ner(note)

colors = {"SYMPTOM": "#938CE3", "DRUG": "#7DF6D9", "DISEASE":"#E39B8C"}
options = {"colors": colors} 

spacy.displacy.render(doc, style="ent", options= options, jupyter=True)

