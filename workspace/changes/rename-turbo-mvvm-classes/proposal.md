# Change: Rename BaseViewModel to TurboViewModel in turbo_mvvm

## Why
The current naming convention `BaseViewModel` is inconsistent with the "turbo" branding used throughout the monorepo. It should be prefixed with "Turbo" to match the package naming (`turbo_mvvm`). This improves consistency, discoverability, and aligns with the project's naming conventions.

## What Changes
- **BREAKING**: Rename `BaseViewModel<A>` → `TurboViewModel<A>` in `turbo_mvvm` package
- **BREAKING**: Rename `ViewModelBuilder<T>` → `TurboViewModelBuilder<T>` in `turbo_mvvm` package
- **BREAKING**: Rename `ViewModelBuilderState<T>` → `TurboViewModelBuilderState<T>` in `turbo_mvvm` package
- Rename file `base_view_model.dart` → `turbo_view_model.dart`
- Rename file `view_model_builder.dart` → `turbo_view_model_builder.dart`
- Update all imports, exports, documentation, comments, and examples within the `turbo_mvvm` package

## Impact
- Affected specs: 
  - New capability: "MVVM Pattern" (turbo_mvvm)
- Affected code:
  - `turbo_mvvm/lib/data/models/base_view_model.dart` → `turbo_view_model.dart`
  - `turbo_mvvm/lib/widgets/view_model_builder.dart` → `turbo_view_model_builder.dart`
  - `turbo_mvvm/lib/turbo_mvvm.dart` (exports)
  - `turbo_mvvm/test/` (all test files)
  - `turbo_mvvm/example/` (example code)
  - `turbo_mvvm/README.md`, `turbo_mvvm/CHANGELOG.md`

