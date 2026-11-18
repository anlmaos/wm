# AnimaOS WM

AnimaOS WM is a downstream fork of [Hyprland](https://github.com/hyprwm/Hyprland),
intended as the window manager for the AnimaOS agentic desktop.

## Tracking upstream

The fork deliberately keeps two local commits on top of upstream `main`:

- `pointer: re-apply cursor on DPMS wake` — bug fix.
- `chore: brand the project as AnimaOS WM` — branding only.

To pull in upstream work:

```sh
git fetch upstream
git merge upstream/main
```

Because the branding changes are small and localized, upstream commits should
merge cleanly. Keep fork-specific commits focused and avoid editing upstream
churn hotspots (notably `src/i18n/Engine.cpp`).

## Compatibility shims (intentionally not renamed)

The following keep their upstream `Hyprland` / `hypr` / `HYPRLAND_*` names so
that upstream code, clients, plugins and tooling keep working:

- build targets and installed binaries (`Hyprland`, `hyprland` symlink, `hyprctl`, `hyprpm`, `start-hyprland`);
- config location `~/.config/hypr/` and `hyprland.lua`;
- `HYPRLAND_*` environment variables and the runtime/socket/lock paths under `$XDG_RUNTIME_DIR/hypr/`;
- session IDs, `DesktopNames=Hyprland`, systemd unit names and the portal configuration;
- Wayland protocol namespaces, pkg-config name `hyprland`, and the plugin ABI.

User-visible names ("AnimaOS WM") live in the CMake project/CPack name, README,
desktop entry names, systemd session description, `hyprctl version` output,
startup splash and crash reports.
