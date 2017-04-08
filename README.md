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

AchivementTypes
----
* __Persistent__ : 게임 플레이 전체에 걸쳐서 달성/공유되는 업적
  * 10번 부활했다.
  * 보유 골드가 10,000원을 넘었다.
* __Session__ : 한 게임 세션 안에서 달성해야 하는 업적
  * 한번도 죽지 않고 클리어했다.
  * 한 게임에서 스킬을 10번 사용했다.
