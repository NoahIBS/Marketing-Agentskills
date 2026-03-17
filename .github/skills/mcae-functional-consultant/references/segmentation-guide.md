# Segmentation and Dynamic Lists in Account Engagement

## Dynamic Lists Overview

Dynamic lists are segment-based lists that automatically add/remove prospects based on rules.

### Creating a Dynamic List

1. **Access:** Marketing → Segmentation → Lists (or Prospects → Segmentation → Segmentation Lists in Lightning)
2. **Type:** Select "Dynamic List" (not public, unless on preference center)
3. **Set Rules:** 
   - Match All (AND) or Match Any (OR) conditions
   - Add conditions based on prospect fields
4. **Preview:** See prospect count matching criteria
5. **Run Rules:** Activate to populate list

### Common Segmentation Criteria

| Criteria Type | Examples |
|---|---|
| **Prospect Fields** | Industry, Country, Job Title, Company Size |
| **Engagement** | Email opened/clicked, Form submitted, Landing page visited |
| **Custom Fields** | Confirmed Opt-In, Lead Status, Scoring buckets |
| **Behavioral** | Days since last engagement, Page views, Score ranges |
| **Campaign Member** | Member of specific campaign, Campaign member status |

### Example: Confirmed Opt-In Segmentation

```
List 1: "Not Confirmed"
  - Prospect custom field: Confirmed Opt-In is NOT True
  - AND Prospect form: Signup Form was completed successfully

List 2: "Confirmed Opt-In"  
  - Prospect custom field: Confirmed Opt-In is True
```

## Use Cases

1. **Opt-In Management:** Separate confirmed from unconfirmed subscribers
2. **Lead Qualification:** Segment by ICP criteria (industry, revenue range)
3. **Engagement Based:** High engagers vs. inactive prospects
4. **Content Targeting:** Segment by role/industry for personalization
5. **Score-Based:** Segregate sales-ready leads from nurturing candidates

## Best Practices

- Keep rules simple and maintainable
- Use AND logic for more precise targeting, OR for broader reach
- Preview before running to validate logic
- Document rule purpose and owner
- Review periodically to ensure accuracy
- Use for both automation and reporting
