# ECR Audit Application - Quick Start Guide

## 🚀 Get Started in 5 Minutes

### Step 1: Import the Application
1. Go to [Power Apps Maker Portal](https://make.powerapps.com)
2. Click **Apps** → **Import canvas app**
3. Upload: `ECR Data Collector - Enhanced.msapp`
4. Click **Import** and wait for completion

### Step 2: Connect Data Source (Required)
1. Open the app in **Edit mode**
2. Go to **Data** panel (left sidebar)
3. Click **+ Add data**
4. Select **SharePoint**
5. Enter site: `https://choctawnationofoklahoma.sharepoint.com/sites/environmentalcompliance`
6. Find and add: **ECR Housing Sites**
7. Click **Connect**

### Step 3: Test the New Features
1. **Play** the app (▶️ button)
2. Try the **Desktop Review**:
   - Select a facility
   - Answer a few questions
   - Click **Save** 
   - ✅ Should see success message
3. Try the **AST Review**:
   - Select a facility and tank
   - Answer questions with Pass/Minor/Major
   - Watch score calculate
   - Click **Save**
   - ✅ Should see success message

### Step 4: Publish
1. Click **File** → **Save**
2. Click **Publish**
3. Share with your team!

---

## 📱 Using the Application

### Main Menu - 5 Options

1. **🏢 ECR - CNO Facilities**
   - Standard environmental compliance review
   - Use for casinos, offices, facilities
   - Goes through existing ECR workflow

2. **🏘️ ECR - Housing Sites**
   - Specialized for housing inspections
   - 55 housing-specific questions
   - Saves to ECR Housing Sites library

3. **📋 ECR Desktop Review**
   - PRE-AUDIT desk review (before site visit)
   - 22 questions about permits, records, history
   - Saves to ECR Desktop Reviews library
   - **TIP**: Complete this BEFORE going to facility

4. **⛽ AST/SPCC Tank Inspection**
   - Tank integrity and SPCC compliance
   - 35 detailed questions
   - Pass/Minor/Major findings
   - Automatic scoring

5. **💧 SWPPP Audit**
   - Coming soon (currently disabled)

---

## 💡 Best Practices

### Desktop Review Workflow
```
1. Schedule facility audit
2. Complete Desktop Review (22 questions) in office
3. Review permits, previous findings, records
4. Save Desktop Review to SharePoint
5. Go to facility for on-site ECR
6. Desktop Review data auto-loads when you select facility
```

### AST Review Workflow
```
1. Identify facility with tanks
2. Select facility in AST Review screen
3. Select tank(s) to inspect
4. Choose inspection type (AST/SPCC/Combined)
5. Complete 35 questions (8 categories)
6. Review calculated score
7. Save to SharePoint
```

### Housing ECR Workflow
```
1. Select housing site from dropdown
2. Complete 55 housing-specific questions:
   - Property condition
   - Waste management  
   - Water/septic systems
   - Safety hazards
   - Mold/moisture
   - Environmental compliance
3. Save to ECR Housing Sites library
```

---

## 🆘 Troubleshooting

### "Can't save to SharePoint"
- **Check**: Are you connected to the network?
- **Check**: Do you have write permissions to the library?
- **Fix**: Go to Data panel, refresh the connection

### "ECR Housing Sites not found"
- **Problem**: Data source not connected
- **Fix**: Follow Step 2 above to add the data source

### "Desktop Review not auto-loading"
- **Check**: Was Desktop Review completed within past 90 days?
- **Check**: Did you select the same facility?
- **Note**: Auto-load only works for recent reviews

### App runs slow
- **Try**: Close and reopen the app
- **Try**: Clear browser cache
- **Check**: Internet connection speed

---

## 📊 What Data Goes Where

| Audit Type | SharePoint Library/List | Key Columns |
|------------|------------------------|-------------|
| Desktop Review | ECR Desktop Reviews | Facility, Audit Date, Auditor, Questions |
| Standard ECR | Audit Reports | Facility, Date, Score, Findings |
| Housing ECR | ECR Housing Sites | Housing Site, Review Date, Questions |
| AST/SPCC | SPCC and AST Reviews | Facility, Tank Type, Score, Pass/Fail |
| Corrective Actions | ECR Corrective Actions | Finding, Facility, Status, Due Date |

---

## 🎓 Training Tips

### For New Auditors
1. Start with **Desktop Review** - it's the simplest
2. Practice on a test facility first
3. Review questions before going to site
4. Take photos for major findings (camera button)

### For Managers
1. Review Desktop Reviews before approving site visits
2. Check SPCC and AST Reviews library for tank inspections
3. Monitor ECR Housing Sites for housing compliance
4. Use SharePoint views to filter by date, facility, auditor

---

## 📈 Reporting & Analytics

### SharePoint Views to Create
1. **Desktop Reviews - Pending Follow-up**
   - Filter: Where "Needs Review" responses exist
   
2. **AST Reviews - Failed Inspections**
   - Filter: Pass/Fail = "Fail"
   - Group by: Facility

3. **Housing Sites - By District**
   - Group by: District
   - Sort by: Review Date descending

### Power BI Integration
Connect Power BI to these SharePoint lists for:
- Compliance trending
- Facility risk scores
- Finding frequency analysis
- Audit completion rates

---

## 🔐 Security & Permissions

### Required Permissions
- **Read**: Facility Contact List, Chemical Products, Generators/ASTs/USTs
- **Write**: Audit Reports, ECR Corrective Actions, ECR Desktop Reviews, SPCC and AST Reviews, ECR Housing Sites

### User Roles
1. **Auditors**: Can create and save all audit types
2. **Managers**: Can review and approve audits
3. **Viewers**: Read-only access to reports

---

## 📝 Customization Guide

### To Add/Modify Questions

#### Desktop Review Questions
1. Edit: `Src/scrDesktopReview.pa.yaml`
2. Find: `ClearCollect(colDesktopQuestions,`
3. Add new question: `{Section: "Your Section", Question: "Your question?", ID: "DR##", Response: "", Notes: ""}`

#### AST Review Questions
1. Edit: `Src/scrASTReview.pa.yaml`
2. Find: `ClearCollect(colASTQuestions,`
3. Add new question: `{Category: "Your Category", Question: "Your question?", ID: "AST##", Finding: "", Severity: ""}`

### To Change Scoring
1. Edit: `Src/App.pa.yaml`
2. Find: `gblScoringWeights`
3. Modify: `Major:`, `Minor:`, `Observation:` values

---

## 🔄 Regular Maintenance

### Weekly
- Review new audits in SharePoint
- Follow up on major findings
- Ensure corrective actions are progressing

### Monthly
- Check that Desktop Reviews are being used
- Review AST inspection compliance
- Update facility contact information

### Quarterly
- Review question sets - are they still relevant?
- Update scoring weights if needed
- Train new auditors

### Annually
- Review all permissions
- Archive old audits
- Update SPCC plans referenced

---

## 📞 Support Contacts

### Technical Issues
- Power Apps Support: [https://powerapps.microsoft.com/support/](https://powerapps.microsoft.com/support/)
- SharePoint Admin: Your IT Department

### Application Questions
- Review: `IMPLEMENTATION_GUIDE.md`
- Review: `QUESTION_SETS_REFERENCE.md`
- Review: `ENHANCEMENT_SUMMARY.md`

---

## ✅ Checklist for First Use

- [ ] Import application to Power Apps
- [ ] Connect ECR Housing Sites data source
- [ ] Test Desktop Review (save successfully)
- [ ] Test AST Review (save successfully)
- [ ] Test standard ECR (verify auto-load works)
- [ ] Verify data appears in SharePoint
- [ ] Share app with team
- [ ] Train users on new features
- [ ] Create SharePoint views for reporting
- [ ] Document your workflow preferences

---

## 🎯 Success Metrics

After implementation, you should see:
- ⬆️ **Faster audits** - Desktop Review reduces site time
- ⬆️ **Better data** - Consistent questions = better comparison
- ⬆️ **More audits** - Streamlined process = more coverage
- ⬇️ **Fewer errors** - Auto-population reduces manual entry
- ⬇️ **Less rework** - Caught issues early in Desktop Review

---

## 🌟 Pro Tips

1. **Complete Desktop Reviews on Friday** for Monday site visits
2. **Use tablet for site visits** - easier than phone for photos
3. **Save drafts frequently** - don't lose your work
4. **Review previous findings first** - check for recurring issues
5. **Take photos liberally** - document everything visual

---

**Need More Help?**
- Read: `IMPLEMENTATION_GUIDE.md` for technical details
- Read: `QUESTION_SETS_REFERENCE.md` for all questions
- Read: `ENHANCEMENT_SUMMARY.md` for complete feature list

**Ready to Go?**
Import the app and start with a Desktop Review today! 🚀
