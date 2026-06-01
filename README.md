# Take-a-Break-Bozo

Android-first mobile app concept for screen-time moderation and healthy break habits.

## Core goals
- Trigger alarms for focused sessions and breaks (example: **45 min screen time + 5 min break**).
- During breaks, show simple exercise challenges (example: **Do 5 push-ups**).
- Keep all user data local on device (no backend, no authentication).

## Planned features (MVP)
1. **Custom timers**
   - Configure focus duration (minutes).
   - Configure break duration (minutes).
2. **Alarm customization**
   - Choose system/default sound.
   - Apply custom alarm sound from local device media.
3. **Challenge customization**
   - Disable challenges entirely.
   - Use preset challenges.
   - Create and maintain custom challenge items.
   - Shuffle and show one challenge at break start.
4. **Theme support**
   - Dark theme as default.
   - Optional light theme switch.

## Bonus features
- Random health/time-management tips shown during countdowns.
- Streak counter for completed breaks/challenges.
- Optional streak exclusions:
  - weekends
  - user-defined custom date periods

## Functional requirements
- App runs fully offline after install.
- No account system and no cloud sync in current scope.
- Local persistence stores:
  - timer settings
  - alarm sound URI/reference
  - challenge list and challenge-enabled state
  - theme preference
  - streak configuration and counts
  - tip display preferences

## Suggested technical direction (Android)
- **UI**: Jetpack Compose
- **Scheduling**: WorkManager + foreground notifications (or AlarmManager for strict alarms)
- **Local persistence**:
  - DataStore for user preferences
  - Room for challenge/tip/streak records
- **Architecture**: MVVM (ViewModel + repository)

## Initial user flow
1. User opens app and sets focus/break durations.
2. User picks alarm sound and challenge mode (off/preset/custom).
3. User starts session countdown.
4. At focus end: alarm + break screen appears.
5. Break screen shows one random enabled challenge and optional tip.
6. Completing break updates streak based on exclusion rules.
