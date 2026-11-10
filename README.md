# MazimealAI

## Sample inputs:

## Sample Raw Bio-Availability Input :

| rule_id | rule_name | rule_type | trigger_food_pattern | trigger_code | target_nutrient_or_outcome | target_code | action | action_code | mechanism | recipe_engine_instruction | conditions_and_limits | population_scope | evidence_tier | evidence_summary | automation_status | source_title | source_type | source_url | review_date |
|---------|-----------|-----------|----------------------|--------------|----------------------------|-------------|--------|------------|-----------|---------------------------|-----------------------|-----------------|---------------|------------------|-------------------|--------------|-------------|------------|-------------|
| BIO-001 | UV-expose mushrooms | processing | fresh mushrooms | ING_MUSHROOM | vitamin D2 | NUT_VITD2 | Expose gill side to sunlight or UV-B before cooking | PROC_UV_EXPOSE | UV converts ergosterol to vitamin D2 | If mushrooms are present and vitamin D optimization is requested, suggest verified UV-treated mushrooms or a user-facing sunlight step. | Vitamin D increase varies by species, UV dose, orientation, and storage; do not estimate a nutrient amount without product/lab data. | general | A | Human food-composition evidence and review evidence consistently show UV exposure raises mushroom vitamin D2. | instruction_only | Vitamin D Mushrooms: Comparison of the Composition of Button Mushrooms Grown in Sunlight or UV Light | peer-reviewed review | https://pubmed.ncbi.nlm.nih.gov/30568833/ | 2026-09-17 |
| BIO-002 | Crush garlic and rest before heating | processing | garlic | ING_GARLIC | allicin formation | CMP_ALLICIN | Crush or mince; rest about 10 minutes before heating | PROC_CRUSH_REST | Tissue disruption lets alliinase convert alliin to allicin; heat can inactivate alliinase | When garlic is cooked, place crushing/mincing before a short rest, then add later or cook gently. | Allicin is unstable; do not promise a clinical dose. Five minutes may help, but about 10 minutes is the more conservative recipe instruction. | general | B | Controlled food-processing studies show crushing before heating preserves more thiosulfinate-forming potential than heating intact garlic. | recipe_safe | Heating garlic inhibits its anticancer properties | peer-reviewed animal/food-processing study | https://pubmed.ncbi.nlm.nih.gov/11160543/ | 2026-09-17 |

### Example Fact selection by the BIO Agent

```json
{
  "rule_id": "BIO-002",
  "rule_name": "Crush garlic and rest before heating",
  "category": "bioavailability",
  "action": {
    "description": "Crush or mince; rest about 10 minutes before heating",
    "code": "PROC_CRUSH_REST",
    "engine_instruction": "When garlic is cooked, place crushing/mincing before a short rest, then add later or cook gently."
  },
  "evidence": {
    "tier": "B",
    "summary": "Controlled food-processing studies show crushing before heating preserves more thiosulfinate-forming potential than heating intact garlic.",
    "sources": [
      {
        "title": "Heating garlic inhibits its anticancer properties",
        "type": "peer-reviewed animal/food-processing study",
        "url": "https://pubmed.ncbi.nlm.nih.gov/11160543/",
        "review_date": "2026-09-17"
      }
    ]
  }
}
```


## Sample Raw Synergies :
| rule_id | rule_name | rule_type | trigger_food_pattern | trigger_code | target_nutrient_or_outcome | target_code | action | action_code | mechanism | recipe_engine_instruction | conditions_and_limits | population_scope | evidence_tier | evidence_summary | automation_status | source_title | source_type | source_url | review_date |
|---------|-----------|-----------|----------------------|--------------|----------------------------|-------------|--------|------------|-----------|---------------------------|-----------------------|-----------------|---------------|------------------|-------------------|--------------|-------------|------------|-------------|
| SYN-001 | Vitamin C with nonheme iron | pairing | plant iron source | NUT_NONHEME_IRON | iron absorption | NUT_IRON | Add a vitamin C-rich food in the same meal | PAIR_VITC_IRON | Ascorbic acid reduces ferric to ferrous iron and forms soluble complexes | Pair beans, lentils, tofu, fortified grains, or greens with citrus, peppers, tomato, or broccoli. | Meal effect depends on dose and matrix; do not apply to heme iron as if equivalent. | general; especially useful in plant-forward diets | A | Human absorption research and NIH guidance identify vitamin C as an enhancer of nonheme iron absorption. | recipe_safe | Iron: Fact Sheet for Health Professionals | government evidence | https://ods.od.nih.gov/factsheets/Iron-HealthProfessional/ | 2026-09-17 |
| SYN-002 | Dietary fat with carotenoids | pairing | carotenoid-rich vegetables | NUT_CAROTENOIDS | carotenoid absorption | NUT_CAROTENOIDS | Include a modest amount of fat in the meal | PAIR_FAT_CAROTENOID | Fat supports micelle formation and intestinal uptake | Add olive oil, avocado, nuts, seeds, tahini, or another compatible fat to salads/vegetables. | Do not add unlimited calories; optimize within the user’s energy and fat constraints. | general | A | Randomized meal studies show higher carotenoid absorption when vegetables are consumed with fat. | recipe_safe | Carotenoid absorption from salad and the effect of salad dressing fat | peer-reviewed human trial | https://pubmed.ncbi.nlm.nih.gov/15277161/ | 2026-09-17 |

### Example Fact selection by the SYN Agent
```json
{
  "rule_id": "SYN-001",
  "rule_name": "Vitamin C with nonheme iron",
  "category": "synergy",
  "action": {
    "description": "Add a vitamin C-rich food in the same meal",
    "code": "PAIR_VITC_IRON",
    "engine_instruction": "Pair beans, lentils, tofu, fortified grains, or greens with citrus, peppers, berries, tomato, or broccoli."
  },
  "evidence": {
    "tier": "A",
    "summary": "Human absorption research and NIH guidance identify vitamin C as an enhancer of nonheme iron absorption.",
    "sources": [
      {
        "title": "Iron: Fact Sheet for Health Professionals",
        "type": "government evidence summary",
        "url": "https://ods.od.nih.gov/factsheets/Iron-HealthProfessional/",
        "review_date": "2026-09-17"
      }
    ]
  }
},
```


## Recipe example input:
Grilled Teriyaki Burgers                                                                                                                                                                          Ingredients:                                                                                              
     - soy sauce                                                                                               
     - honey                                                                                                   
     - garlic                                                                                                  
     - ginger                                                                                                  
     - mayonnaise                                                                                              
     - salt                                                                                                    
     - pepper                                                                                                  
Steps:                                                                                                    
     1. Stir together first 4 ingredients.                                                                     
     2. Stir 2 teaspoons soy sauce mixture into mayonnaise, and set aside.                                     
     3. Combine 1/3 cup soy sauce mixture, beef, salt, and pepper; shape into 6 patties.                       
     4. Brush with remaining soy sauce mixture.                                                                
     5. Grill over medium-high heat (350°-400°) 4 minutes on each side or until beef is no longer pink.        
     6. Coat cut sides of buns with cooking spray, and grill, cut side down, 2 minutes.                        
     7. Spread buns evenly with mayonnaise mixture, and fill with the patties.     



## General Optimization Sequence Flow : 
<img width="1568" height="1234" alt="image" src="https://github.com/user-attachments/assets/470ca7f9-9e15-4835-a469-281e4182c465" />


