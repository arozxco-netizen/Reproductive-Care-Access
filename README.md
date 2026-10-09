// ============================================================
// PUBH 402 — Systems Map Submission (.gv)
// Team Members: Mitchel Gonzalez, Brooke Granger, Sienna Hernandez, 
//               Arelie Orozco, Anthony Vuongo
// Health Problem: Access to Reproductive Care Including Abortion
// ============================================================

digraph ReproductiveCareAccess {

    rankdir=TD;
    node [shape=box, style="rounded, filled", fillcolor="white", fontname="Arial"];

    // ============================================================
    // --- Selected 12 System Elements (Nodes) ---
    // ============================================================

    income_security [label="Income security"];  // Category: Structural Determinants
    occupational_stratification_by_race_gender [label="Occupational stratification by race and gender"];  // Category: Structural Inequities
    medicaid_enrollment [label="Medicaid enrollment"];  // Category: Financing / Insurance
    household_out_of_pocket_spending [label="Household out-of-pocket spending"];  // Category: Funding
    bundled_payment_use [label="Bundled payment use"];  // Category: Payment Models
    state_scope_of_practice_laws [label="State scope-of-practice laws"];  // Category: Federal and State Policy
    reimbursement_requirements [label="Reimbursement requirements"];  // Category: Enforcement and Accountability
    primary_care_clinician_supply [label="Primary care clinician supply"];  // Category: Workforce
    obstetric_maternity_care_availability [label="Obstetric/maternity care availability"];  // Category: Infrastructure
    medical_device_availability [label="Medical device availability"];  // Category: Pharmaceuticals and Devices
    specialty_care_referral_availability [label="Specialty care referral availability"];  // Category: Care Providers
    health_communication_effectiveness [label="Health communication effectiveness"];  // Category: Public Health


    // ============================================================
    // --- Structural Input Driver ---
    // ============================================================

    // Racial and gender concentration in low-wage hourly jobs directly depresses household income security.
    occupational_stratification_by_race_gender -> income_security [label="-"];


    // ============================================================
    // --- Provisional Feedback Loops (1 Per Team Member) ---
    // ============================================================

    // ------------------------------------------------------------
    // Loop 1 (Mitchel Gonzalez) — Clinical Workforce & Specialty Loop (Reinforcing)
    // ------------------------------------------------------------
    // Higher primary care supply increases capacity to initiate timely specialty referrals.
    primary_care_clinician_supply -> specialty_care_referral_availability [label="+"];

    // Efficient specialty referrals support and sustain regional obstetric/maternity facilities.
    specialty_care_referral_availability -> obstetric_maternity_care_availability [label="+"];

    // Robust regional maternity infrastructure attracts and retains primary care clinicians.
    obstetric_maternity_care_availability -> primary_care_clinician_supply [label="+"];


    // ------------------------------------------------------------
    // Loop 2 (Brooke Granger) — Scope of Practice & Policy Loop (Reinforcing)
    // ------------------------------------------------------------
    // Expanded state scope-of-practice laws allow APCs to practice, increasing primary care supply.
    state_scope_of_practice_laws -> primary_care_clinician_supply [label="+"];

    // A larger clinician workforce improves patient education and public health outreach.
    primary_care_clinician_supply -> health_communication_effectiveness [label="+"];

    // Effective health communication drives public advocacy that pressures lawmakers to expand scope laws.
    health_communication_effectiveness -> state_scope_of_practice_laws [label="+"];


    // ------------------------------------------------------------
    // Loop 3 (Sienna Hernandez) — Socioeconomic Financial Trap Loop (Reinforcing)
    // ------------------------------------------------------------
    // Lower income security increases eligibility and enrollment in state Medicaid programs.
    income_security -> medicaid_enrollment [label="-"];

    // Hyde Amendment coverage exclusions force Medicaid enrollees to pay out-of-pocket for abortion care.
    medicaid_enrollment -> household_out_of_pocket_spending [label="+"];

    // High out-of-pocket costs force reliance on clinics requiring upfront bundled cash payments.
    household_out_of_pocket_spending -> bundled_payment_use [label="+"];

    // Substantial lump-sum bundled fees drain household liquid savings, further reducing income security.
    bundled_payment_use -> income_security [label="-"];


    // ------------------------------------------------------------
    // Loop 4 (Arelie Orozco) — Administrative Burden & Communication Loop (Reinforcing)
    // ------------------------------------------------------------
    // Onerous reimbursement rules increase clinic overhead, forcing facility cutbacks or closures.
    reimbursement_requirements -> obstetric_maternity_care_availability [label="-"];

    // Active maternity clinics serve as trusted hubs for delivering clear health communication.
    obstetric_maternity_care_availability -> health_communication_effectiveness [label="+"];

    // Effective public communication and advocacy pressure regulatory agencies to streamline reimbursement rules.
    health_communication_effectiveness -> reimbursement_requirements [label="-"];


    // ------------------------------------------------------------
    // Loop 5 (Anthony Vuongo) — Infrastructure & Device Supply Loop (Reinforcing)
    // ------------------------------------------------------------
    // Available obstetric facilities maintain localized demand and stock of essential clinical devices.
    obstetric_maternity_care_availability -> medical_device_availability [label="+"];

    // Adequate medical devices (MVA kits, ultrasounds) enable specialists to accept and complete referrals.
    medical_device_availability -> specialty_care_referral_availability [label="+"];

    // High specialty referral completion rates improve facility revenues and maintain maternity care availability.
    specialty_care_referral_availability -> obstetric_maternity_care_availability [label="+"];

}
