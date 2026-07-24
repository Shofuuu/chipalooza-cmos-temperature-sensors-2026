# 🏆 Chipalooza Challenge #2 (IHP SG13CMOS5L) - Technical & Schedule Summary 

> [!IMPORTANT]
> **Official Name:** Chipalooza Challenge #2 (IHP SG13CMOS5L) or informally "IHP (1)". 
> **Start Date:** Monday, July 13, 2026. 
> **Tapeout Date:** November 9, 2026. 

> [!WARNING]
> **Schedule Change:** The challenge is 17 weeks long instead of the normal 18 weeks because IHP pulled in the tapeout date by one week. The tapeout date is strictly fixed! 

## 📅 Challenge Schedule 

| Milestone | Date / Week Of | Details |
| :--- | :--- | :--- |
| **Challenge Start** | July 13, 2026 | Official start of the challenge. |
| **Proposals Due** | July 27, 2026 | Deadline for standard proposals. |
| **Late Proposals** | August 10, 2026 | Late exception deadline due to organization process. |
| **Review A: Proposal** | Week of July 27 | Proposal review gating stage. |
| **Review B: Schematic** | Week of Aug 31 | Pre-layout simulation and schematic design review. |
| **Review C: Layout** | Week of Sept 28 | Post-layout simulation and layout design review. |
| **Review D: Final Design** | Week of Oct 19 | Final gating review; designs must be ready for tapeout. |
| **Tapeout Date** | November 9, 2026 | Final submission for fabrication. |

## 📝 Proposal Requirements 

Proposals must be submitted to `chipalooza@opencircuitdesign.com` . Designers may work individually or in teams (preferably ≤ 3 people) . 

**Main Proposal Document (Public-facing, no personal details):** 
- [ ] Type of IP block.
- [ ] List of I/O, including test ports (note where pins may/may not be multiplexed).
- [ ] Functional description.
- [ ] Target specification (average, min, max, absolute limits).
- [ ] Outline of a test plan for validation.

**Sent Separately:** 
- [ ] List of available testing equipment.
- [ ] Designer CVs.

## ⚙️ Technical Details & Specifications 

### Process & Corners
* **Process:** IHP SG13CMOS5L .
* **Digital Voltage:** 1.2V target (standard cells are characterized for 1.08V to 1.65V) .
* **Analog Voltage:** 3.3V supply .
* **Temperature Specs:** -40°C to +125°C characterized. Maximum 110°C is acceptable for post-layout PVT verification if hitting 125°C is difficult .
* **Validation:** Full corner set is assumed available. Magic provides high/low/typical corners for resistance and capacitance extraction .

### Available Resources
* **Voltages:** 1.2V bandgap .
* **Voltage References:** Up to 2 bandgap-referenced bias voltages. (Low scale: 0.3V-2.4V in 0.3V steps; High scale: 0.4V-3.2V in 0.4V steps) .
* **Current References:** Up to 2 bandgap-referenced current sources (5-bit iDAC with 32 values over 4 scales: 50nA min to 10.32uA max) .
* **Digital Control/Test:** Up to 16 signals (May evolve into a shared 32-bit bus + dedicated project power/enable signals) .
* **Pin Sharing:** Pads can be dedicated or shared. Mux switch resistance and power waffle pFETs can be sized as low as reasonably needed .

### Slot & Wrapper 
* **Budgeted Chip Area:** ~10mm² .
* **Estimated Slot Size:** ~750µm × 340µm (Based on 10mm² upscaling, though previous 520µm × 250µm slots may suffice) .
* **Wrapper:** Designers must wire their IP block inside the template wrapper cell restricted to the available slot size . Up to 16 designs can be accommodated on a single test chip . 

### Packaging Options (TBD)
* **QFN Package:** Standard 64-pad frame (preferred if available from IHP) .
* **Wafer.Space Board:** 140-pin mezzanine connector (potential dev board akin to Chip Foundry Caravel, if assembled break-out boards are available) .

## 🛠️ Tools, Templates & Repositories 

> [!WARNING]
> **Open Source Verification Mandate:** You *can* use commercial tools or AI to design, but the project **MUST** be verifiable as meeting specs using open source EDA tools (e.g., KLayout, Xschem). Failure to do so will result in rejection. 

### Repositories & Licensing
* **Hosting:** Must be in a public git repo (GitHub, GitLab, Codeberg, etc.) .
* **License:** Standard open-source license, preferably **Apache 2.0**. No violating sources allowed .
* **Content Requirements:** Full behavioral description, all views needed to reproduce/verify the IP, sign-off data (DRC/LVS), and plotted simulation summaries (avoid unnecessary raw data dumps) .
* **Plain Text/Makefiles:** Simple markdown, key/value pairs, or template makefiles will be required for automated handling and top-level integration (e.g., `make run-drc`) .

### Useful Links & Frameworks
* **IIC-OSIC-TOOLS:** July release concentrates heavily on `ihp-sg13cmos5l` (fixes KLayout LVS without ntap/ptap devices) .
* **FSiC Slides:** [From idea to tapeout: open-source AMS design flow](https://wiki.f-si.org/index.php?title=From_idea_to_tapeout:_an_open-source_analog_mixed-signal_design_flow_with_the_IHP_Open-PDK) 
* **Template Repo:** [ihp-sg13g2-ams-chip-template](https://github.com/iic-jku/ihp-sg13g2-ams-chip-template) *(Note: Porting to ihp-sg13cmos5l is a WIP)* 
* **Tutorial:** [IHP AMS Chip Template Tutorial](https://iic-jku.github.io/ihp-sg13g2-ams-chip-template/index.html) 
* **HeiChips Workshops:**
  * [Analog Workshop](https://github.com/HeiChips/heichips26-analog-workshop) 
  * [Digital Workshop](https://github.com/HeiChips/heichips26-digital-workshop) 