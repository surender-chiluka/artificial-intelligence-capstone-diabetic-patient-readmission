<B><H1>Capstone project </H1></B>
Professional Certificate in Machine Learning and Artificial Intelligence - May 2023 offered via emeritus.org
<B><H1>Business Objective</H1></B>
Identify the probability that a diabetic patient will be readmitted with in less than 30 days after discharge from hospital
<B><H2>About Data</H2></B>
<div class="alert alert-block alert-success">
    <ul>
        <li><a href="https://www.w3schools.com">Diabetic patients readmission for 1999 – 2008</a> available at UC Irvine Machine Learning Repository</li>
        <li>10 years, from 1999 to 2008, of clinical data of inpatient </li>
        <li>Collected for 130 US hospitals and integrated delivery networks  </li>
        <li>Data of patients 
            <ul>
                <li>Diagnosed with diabetes</li>
                <li>Underwent laboratory test</li>
                <li>Took medications during their stay</li>
                <li>Stayed up to 14 days</li>
            </ul>
        </li>
        <li> Sample size: 101766
            <ul> 
                <li>Features: 47 such as admission and discharge type, length of stay, diagnosis, lab tests and medication</li>
                <li>Features: 47 such as demographics, admission and discharge type, length of stay, diagnosis, lab tests and medication</li>
                <li>Has both Numerical and Categorical data</li>
                <li>Data does not contain null values but we have unknown/invalid and ? values</li>
            </ul>
        </li>
    </ul>
</div>
<div class="alert alert-block alert-success">
    <B><H2>Data Analysis</H2></B>
    <ul>
        <li><B>Features that will not have any data modifications or cleaning</B>
            <ul>
                <li>Medication Change (change)
                  <ul>
                    <li>54% no change in medication</li>
                    <li>46% change in medication</li>
                  </ul>
                </li>
                <li>Diabetic medication prescribed (diabetesMed)
                  <ul>
                    <li>23% not prescribed to diabetic medication</li>
                    <li>77% prescribed to diabetic medication</li>
                  </ul>
                </li>
                <li>Number of Days between Admission and Discharge (time_in_hospital)
                  <ul>
                    <li>Data is for patients in the hospital up to 14 days</li>
                    <li>3 days is highest closelly follwed by 2 day. After 3 days, the numbers dropped   </li>
                    <li>Only 10% of the data for 8 day or more</li>
                  </ul>
                </li>
                <li>Number of non lab procedures (num_procedures)
                  <ul>
                    <li>0 to 6 procedures</li>
                    <li>20% have 1 and the other 4 are between 5% to 13%</li>
                  </ul>
                </li>
            </ul>
        </li>
        <li><B>Features that will be dropped</B>
            <ul>
                <li>Encounter Id(encounter_id)      : This is just ID value</li>
                <li>Unique Patient Id(patient_nbr)  : We are modeling based on encounter and not based on individual patient</li>
                <li>Patient Weight (weight)
                  <ul>
                    <li>97% values are ? meaning its not avaiable or not recorded</li>
                    <li>Thus decided not to use</li>
                  </ul>
                <li>Secondary diagnosis codes (diag_2, diag_3)
                  <ul>
                    <li>First 3 digits of secoundary diagnosis ICD9 codes</li>
                    <li>diag_2 have 923 unique values</li>
                    <li>diag_3 have 954 unique values</li>
                    <li>Because of the number of unique values decided to drop</li>
                    <li>Also priary diagnosie code is also avaiable</li>
                  </ul>
                <li>Admitting Physician specialty (medical_specialty)
                  <ul>
                    <li>72 Unique values</li>
                    <li>50% is ? (looks like ? is used for null)</li>
                    <li>4 values are almost 35%</li>
                    <li>Considered to shrink to the top few values and all remaning set to other</li>
                    <li>Becasue of the % of missing data, decided to drop</li>
                  </ul>
                <li>Max Glucose Serum Test results (max_glu_serum)
                  <ul>
                    <li>Not avaiable for 95% </li>
                    <li>Becasue of the % of missing data, decided to drop</li>
                  </ul>
              <li>Unique 23 Payer Codes (payer_code)
                  <ul>
                    <li>Not avaiable for 95% </li>
                    <li>40% missing data</li>
                    <li>30% is of one provdier code MC (Probably Medicare)</li>
                    <li>Becasuse of missing data and only one other code used so much, decided to droped thie feature</li>
                  </ul>
            </ul>
        </li>
        <li><B>Drop outlier patient records</B>
            <ul>
                <li>Admission Type Id(admission_type_id): Drop new born patients</li>
                <li>Number of diagnoses(number_diagnoses): Drop patient records with 1 or above 9 number of diagnoses</li>
                <li>Number of Lab procedures (num_lab_procedures): Drop patient with more than 98 procedures</li>
                <li>Patient Gender (gender): Drop patient with Unknown/Invalid race</li>
                <li>Patient Age (age): Drop patient under 10 years</li>
            </ul>
        </li>
        <li><B>Feature Value Changes</B>
             <ul>
               <li>A1Cresult</li>
                <li>Patient Race (race): Patient other than African American or Caucasian will be changed to Other</li>
                <li>Number of medications administered (num_medications): Patients with more than 40 medications are updated to 40 medications</li>
                 <li>Patient admission info (admission_source_id): Feature compressed to 3 different values - Emergency, Physician referral, Other</li>
                 <li>Patient discharge info (discharge_disposition_id): Feature compressed to 4 different values - Home, Expired, Referred, Other</li>
                 <li>Number of Outpatient visits in last 1 year (number_outpatient): Changing from number to visited or not</li>
                 <li>Number of Inpatient visits in last 1 year (number_inpatient): Changing from number to visited or not</li>
                 <li>Number of Emergency visits in last 1 year (number_emergency): Changing from number to visited or not</li>
                 <li>Admission Type Id(admission_type_id): Not Available, NULL, Not Mapped, Trauma Center changed to Other</li>
                  <li>Medications: 23 medication features are updated to either used or not
                      <ul>
                          <li>After modelling an further analyisi</li>
                          
                      </ul>
                 </li>

            </ul>
        </li>
        <li><B>Classification Feature</B>
             <ul>
                 <li>Readmitted: Changed to 1 for readmitted in less than 30 days, otherwise 0</li>
            </ul>
        </li>
    </ul>
</div>
   
