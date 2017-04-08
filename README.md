Achievements.ue4
====

정형화된 업적 체크 시스템 제공


Define your achievements
----
```c++
// 하드 난이도에서 한번도 죽지 않고 플레이
auto cond = AchivementCondition()
  .Flag("death", false)
  .Value("difficulty", [](long v) { return v == Difficulty::Hard });
  
UAchievement::AddAchievement(
  AchievementType::Session,
  "EXPERT", ACHIEVEMENT_ID_EXPERT,
  cond);
```

Set achievement values
----
```c++
void OnDamaged() {
    _SET_FLAG("death", true);
    _INCREMENT("revival_count", 1);

    /* ... revive player ... */
}
```
