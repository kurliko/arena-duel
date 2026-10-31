# Arena Duel

Projekt zespołowy (Godot 4.7.2 .NET, GDScript, RL przez godot_rl_agents + SB3). Pełny kontekst i wymagania: @docs/project-context.md

## Zasady
- GDScript ze statycznym typowaniem, jedna klasa na plik, `class_name` dla klas wielokrotnego użytku.
- Logika w `_physics_process`, stały krok 60 Hz. Parametry tylko w `GameConfig`, bez magicznych liczb.
- Mózgi (`Brain`) widzą wyłącznie `Observation` i zwracają `Action`, bez odwołań do węzłów sceny.
- Wspólna przestrzeń akcji jest dyskretna (`Action`): ruch 0..8, obrót 0..4 (z precyzyjnym), strzał, unik.
- Zachowania wysokiego poziomu (atak, szukanie, osłona, unik, amunicja) są we wspólnym `scripts/navigation/behaviors.gd`; mózgi tylko wybierają zachowanie.
- Projekt Godota jest w `godot/`; Python w `training/` i `analysis/`.

## Komendy
- Testy silnika rozmytego: `... --headless --path godot --script res://tests/test_fuzzy.gd` (kod wyjścia 0 = OK)
- Walidacja bez grafiki: `"C:\Tools\Godot\Godot_v4.7.2-stable_mono_win64\Godot_v4.7.2-stable_mono_win64\Godot_v4.7.2-stable_mono_win64_console.exe" --headless --path godot --quit`
- Środowisko: Windows, PowerShell.

## Git
- Commity tylko jako autor z konfiguracji gita (Filip Opacki). Nie dodawaj linii `Co-Authored-By` ani żadnej innej atrybucji Claude/AI w opisach commitów i PR.
- Opisy commitów i PR po angielsku (dokumentacja i komentarze w kodzie zostają po polsku).
- Nie przepisuj historii (rebase, filter-branch, force push) bez wyraźnej zgody: repo jest na GitHubie i mogą je klonować inni.
