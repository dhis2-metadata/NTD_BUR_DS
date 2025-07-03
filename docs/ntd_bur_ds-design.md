# Neglected Tropical Diseases Disease-specific module: Buruli ulcer System Design Guide { #ntd-bur-ds-design }

## Background and Purpose

The **Buruli ulcer (BUR) disease-specific module** builds upon the design principles and implementation guidance outlined in the overarching **Neglected Tropical Diseases (NTD) DHIS2 module**. While the overarching module provides a unified framework for integrating NTD data into national health management information systems (HMIS), this document focuses specifically on the technical design considerations and metadata configuration required for the **routine collection, reporting, and use of Buruli ulcer-related data**.

As with the broader NTD package, the BUR-specific module is aligned with **WHO guidelines and global best practices** for disease surveillance, monitoring, and case management. It supports countries in localizing and adapting the metadata to reflect their national strategies, reporting needs, and clinical workflows. This ensures alignment with local epidemiological realities while enabling countries to contribute to regional and global monitoring efforts.

BUR is a debilitating, necrotizing skin disease that remains a significant public health concern in several endemic regions, often affecting vulnerable populations in remote and underserved areas. The **[WHO 2021–2030 road map for NTDs](https://www.who.int/publications/i/item/9789240062863)** highlights BUR under the strategic objective of improving integrated skin NTD management and reducing disability. The BUR module supports this goal by standardizing data capture and improving visibility on disease trends, clinical outcomes, and treatment access.

This system design guide provides detailed documentation of the **BUR data elements, indicators, datasets, program stages, and relationships** used in the module. It also offers practical recommendations for implementers seeking to **adapt, expand, or integrate** the BUR module into their existing HMIS platforms, ensuring the availability of high-quality data to guide **early detection, case management, and prevention of long-term disability**.

## System Design Overview

### Module Structure

The BUR module is built in a single monthly dataset (NTD-BUR-DS - Buruli ulcer) designed for the **reporting of diseases at the point of care (health facility level)**.

### Burden of Disease Section

The section reports the key surveillance data points to be monitored for reporting. It has a **flat structure** and most DEs are disaggregated by **sex (male and female) and by Global NTD Annual Reporting Form (GNARF) age groups (less than 1y, 1 -4y, 5-14y, 15-24y, 25-49y, 50-64y, 65+ years)**. The deaths are not disaggregated by age or sex.

!(Burden of disease)[resources/image/BUR_001.png]

### Case Classification Section

The **case classification** in the BUR module is structured around three standard WHO-defined categories and is further **disaggregated along the case cascade: Reported, Suspected, Confirmed, and Relapsed**. This allows for a more nuanced understanding of the disease burden and the progression of cases through the surveillance and clinical management process. To ensure data consistency and integrity, the **sum of all disaggregations by case classification must match** the corresponding totals recorded in the initial section for reported, suspected, confirmed, and relapsed cases. This alignment is essential for accurate analysis, program monitoring, and validation of reporting completeness.

!(Case classification)[resources/image/BUR_002.png]

### Treatment Section

The section collects the information on the cases completing a full treatment course disaggregated by confirmed and suspected cases.

!(Treatment completion)[resources/image/BUR_003.png]

### Referral Type Section

The last section of the dataset reports the referred cases disaggregated along the case cascade: Suspected and Confirmed. To ensure data consistency and integrity, the **sum of all disaggregations by case classification must match** the corresponding totals recorded in the initial section for reported, suspected, confirmed, and relapsed cases. This alignment is essential for accurate analysis, program monitoring, and validation of reporting completeness.

!(Referrals)[resources/image/BUR_005.png]

## Dashboard

The BUR module includes a predefined dashboard (NTD - Buruli ulcer).

!(Dashboard)[resources/image/BUR_004.png]

## Special Considerations

### Overarching VS BUR Disease-specific modules

The **Buruli ulcer (BUR) disease-specific module** is designed to **build upon and extend** the foundation established in the **NTD DHIS2 overarching module**. While the overarching module provides a standardized structure for capturing core NTD data across multiple diseases, the BUR module introduces **additional detail and tailored content** specific to the clinical, surveillance, and programmatic needs of Buruli ulcer.

Many of the core elements—such as case notification, demographic details, and basic clinical classifications—**overlap with the metadata in the overarching module**. However, the BUR module adds further granularity, capturing **more disease-specific variables**, such as lesion type, anatomical location, surgical management, and long-term disability monitoring, which are not fully detailed in the general NTD package.

It is important for implementers to note that:

- **If data are being reported through the BUR disease-specific module**, there is **no need to duplicate reporting in the overarching module** for the same data points. The disease-specific module is considered the authoritative source for BUR-related reporting.
- Some **variable names, field structures, or value sets may differ slightly** between the BUR dataset and the overarching module. These differences reflect the need for more context-specific language or reporting detail.
- The **table below provides a side-by-side comparison** of key data elements across the two modules, helping users understand where content overlaps, diverges, or expands in the BUR module.

This modular design allows countries to **gradually scale from generalized NTD reporting to more detailed, disease-focused surveillance** as their systems and programmatic needs evolve, while maintaining coherence and minimizing duplication within DHIS2.

| Overarching Module - BUR section | Disease-specific BUR module     |
| -------------------------------- | ------------------------------- |
| New active cases                 | New reported cases              |
| Recurrent confirmed cases        | Relapsed cases                  |
| New Lab-confirmed cases          | New Lab-confirmed cases         |
| Category III cases               | Category III                    |
| Related deaths                   | Related deaths                  |
| Cases healed with disability     | Cases healed with disability    |
| Cases completing full treatment  | Cases completing full treatment |
| Not present                      | Suspected cases                 |
| Not present                      | Imported cases                  |
| Not present                      | Referred by                     |

### NTD Staff Metadata

Integrating information on health staff and their NTD-specific training into the **Health Facility Profile (HFP)** program—within the broader **Healthcare System Accessibility** domain—greatly enhances the quality and strategic value of health system data. The **[HFP toolkit](https://docs.dhis2.org/en/implement/health/health-facility-profile/design.html#introduction)** in DHIS2 is designed to support structured and routine data collection on facility attributes, including infrastructure, service availability, and workforce readiness. When integrated into the national **HMIS**, this toolkit provides a comprehensive view of service delivery capacity and supports evidence-based planning and response.

To avoid duplication and ensure consistency, it is important to note that a **[dedicated dataset for NTD staff and training information already exists in the NTD overarching module](https://docs.dhis2.org/en/implement/health/neglected-tropical-diseases/ntd-overarching-module/design.html#data-set-ntd-human-resources)**. This dataset includes key variables relevant to workforce capacity for NTD program implementation. Depending on a country’s configuration and workflow preferences, implementers should choose one of the following integration paths:

1. **If using the HFA program** as part of national infrastructure mapping, relevant NTD workforce data—such as the number of trained staff, training types, and date of last training—should be integrated directly into the HFA data collection forms using the toolkit's **dynamic digital questionnaire format**.
2. **f using the NTD Staff dataset from the overarching module**, implementers should ensure that this dataset includes all critical staff-related attributes and is updated regularly. Where appropriate, this dataset can be **linked or cross-referenced with HFA data** to enable unified reporting and reduce fragmentation.

In both cases, the goal is to support **modular and flexible data management**, while ensuring that accurate, up-to-date information on human resources for NTD control is readily available. This enriched and integrated dataset is vital for **resource planning, training program evaluation, and emergency response preparedness**, particularly in endemic and high-risk areas.
