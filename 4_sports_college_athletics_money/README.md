# Topic 4 · College sports money and Title IX

## Files in this folder

| File | One row is | Rows × columns |
| --- | --- | --- |
| **4_college_athletics_eada_2024_25.csv** | A college or university, academic year 2024–25 | 2,037 × 34 |
| data_dictionary.csv | The meaning of every variable | |

This topic has a single CSV, so no join was needed. Each row shows a school's enrollment and athletes by gender, scholarship and recruiting money, coach pay, and revenue and expenses overall and for football and basketball. The unique ID is **unitid** (school names repeat).

**What is the Title IX gap?** Title IX requires equal opportunity in college sports. title9_gap compares the share of athletes who are women with the share of students who are women. If 55% of students are women but only 40% of athletes are, the gap is −15 points.

## All variables

| Variable | Type | Meaning | Values / range | Missing |
| --- | --- | --- | --- | --- |
| unitid | text | Federal school ID (IPEDS). Unique key; school names repeat | 2,037 distinct values, e.g. 100654 | 0 |
| school | text | School name | 2,023 distinct values, e.g. Alabama A & M University | 0 |
| city | text | City | 1,330 distinct values, e.g. Normal | 0 |
| state | text | State or territory (blank for one Canadian school) | 53 distinct values, e.g. AL | 1 |
| division | text | Athletic association and division | 19 distinct values, e.g. NCAA Division I-FCS | 0 |
| sector | text | Public/private and 2-year/4-year | Private for-profit, 4-year or above; Private nonprofit, 2-year; Private nonprofit, 4-year or above; Public, 2-year; Public, 4-year or above; Sector Unknown | 0 |
| students_men | integer | Full-time undergraduate men | 2 to 30,671 | 0 |
| students_women | integer | Full-time undergraduate women | 10 to 32,943 | 0 |
| students_total | integer | Full-time undergraduates (men + women) | 52 to 60,277 | 0 |
| athletes_men | integer | Men athletes (each counted once) | 0 to 787 | 0 |
| athletes_women | integer | Women athletes (each counted once) | 0 to 577 | 0 |
| pct_women_students | decimal | % of undergraduates who are women | 2.6 to 99.9 | 0 |
| pct_women_athletes | decimal | % of athletes who are women | 0 to 100 | 0 |
| title9_gap | decimal | pct_women_athletes − pct_women_students; negative = women under-represented in sports | -74.2 to 47.4 | 0 |
| big_title9_gap | 0/1 flag | 1 if title9_gap is −5 points or worse | 1 = yes (1,690); 0 = no (347) | 0 |
| athletic_aid_men | integer | Athletic scholarship $ to men | 0 to 19,645,560 | 16 |
| athletic_aid_women | integer | Athletic scholarship $ to women | 0 to 20,055,491 | 19 |
| recruiting_men | integer | Recruiting spending $, men's teams | 0 to 5,926,680 | 16 |
| recruiting_women | integer | Recruiting spending $, women's teams | 0 to 1,867,789 | 19 |
| head_coach_pay_mens_teams | integer | Average head coach salary, men's teams, $ per full-time position | 15,000 to 3,486,642 | 16 |
| head_coach_pay_womens_teams | integer | Average head coach salary, women's teams, $ per full-time position | 15,000 to 857,166 | 20 |
| total_revenue | integer | Total athletics revenue, $ | 13,766 to 343,106,827 | 0 |
| total_expenses | integer | Total athletics expenses, $ | 13,766 to 295,265,883 | 0 |
| profit | integer | total_revenue − total_expenses. Often 0: schools count university support as revenue | 0 to 65,693,046 | 0 |
| has_football | 0/1 flag | 1 if the school has football | 1 = yes (876); 0 = no (1,161) | 0 |
| football_revenue | integer | Football revenue, $ | 0 to 195,723,436 | 329 |
| football_expenses | integer | Football expenses, $ | 0 to 93,255,797 | 329 |
| football_profit | integer | football_revenue − football_expenses, $ | -8,609,425 to 113,636,406 | 329 |
| football_makes_money | 0/1 flag | 1 if football revenue > expenses (blank if no football) | 1 = yes (312); 0 = no (564) | 1,161 |
| mens_bball_revenue | integer | Men's basketball revenue, $ | 7,646 to 52,729,506 | 111 |
| mens_bball_expenses | integer | Men's basketball expenses, $ | 7,646 to 31,994,396 | 111 |
| womens_bball_revenue | integer | Women's basketball revenue, $ | 3,441 to 13,119,360 | 180 |
| womens_bball_expenses | integer | Women's basketball expenses, $ | 3,220 to 13,119,360 | 180 |
| ncaa_d1 | 0/1 flag | 1 if NCAA Division I (FBS, FCS, or no football) | 1 = yes (358); 0 = no (1,679) | 0 |

## Things to watch for

- **Trailing spaces in division:** 780 rows end with a space (e.g., "NJCAA Division I "). Trim before grouping.
- **"No football" is coded two ways:** of 1,161 schools without football, 329 have blank football money and 832 have 0.
- **profit is not real profit:** it is exactly 0 for 1,288 schools (63%), because schools record university subsidies as athletics revenue. Similarly, 501 of 876 football schools report football revenue exactly equal to expenses, so most football_makes_money = 0 values mean "reported break-even," not a loss.
- **Use unitid, not school name:** 2,023 names for 2,037 schools (e.g., three different Columbia Colleges).
- **Special cases with extreme gaps:** women's colleges (e.g., Wellesley, 3 men students) and 3 schools reporting more men athletes than men students.
- **One non-U.S. school:** Simon Fraser University (Canada) has no state and sector "Sector Unknown."

## Source

U.S. Department of Education, Office of Postsecondary Education, Equity in Athletics Data Analysis (EADA), "All data combined for academic year 2024–25." https://ope.ed.gov/athletics/#/datafile/list (34 of the original 4,275 columns kept; percentages and yes/no columns added.)
