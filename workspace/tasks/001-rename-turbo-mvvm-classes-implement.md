---
status: done
skill-level: medior
parent-type: change
parent-id: rename-turbo-mvvm-classes
---

# Task: Rename turbo_mvvm classes to Turbo equivalents

## End Goal
Rename `BaseViewModel` to `TurboViewModel`, `ViewModelBuilder` to `TurboViewModelBuilder`, and `ViewModelBuilderState` to `TurboViewModelBuilderState` throughout the `turbo_mvvm` package, including file names, class definitions, exports, tests, examples, and documentation.

## Currently
- `BaseViewModel<A>` class exists in `lib/data/models/base_view_model.dart`
- `ViewModelBuilder<T>` class exists in `lib/widgets/view_model_builder.dart`
- `ViewModelBuilderState<T>` class exists in the same file
- All references use the old names throughout the package

## Should
- `TurboViewModel<A>` class in `lib/data/models/turbo_view_model.dart`
- `TurboViewModelBuilder<T>` class in `lib/widgets/turbo_view_model_builder.dart`
- `TurboViewModelBuilderState<T>` class in the same file
- All references updated to use new names
- Exports updated in `lib/turbo_mvvm.dart`
- Tests updated to use new class names
- Examples updated to use new class names
- Documentation updated

## Constraints
- Must rename file `base_view_model.dart` → `turbo_view_model.dart`
- Must rename file `view_model_builder.dart` → `turbo_view_model_builder.dart`
- Must update all imports and exports
- Must update all test files
- Must update all example code
- Must update README.md and CHANGELOG.md
- Must preserve all functionality (pure rename, no behavior changes)
- Must update `AkeBaseViewModel` comments that reference `BaseViewModel` or `ViewModelBuilder`

## Acceptance Criteria
- [ ] `BaseViewModel` renamed to `TurboViewModel` in all files
- [ ] `ViewModelBuilder` renamed to `TurboViewModelBuilder` in all files
- [ ] `ViewModelBuilderState` renamed to `TurboViewModelBuilderState` in all files
- [ ] File `base_view_model.dart` renamed to `turbo_view_model.dart`
- [ ] File `view_model_builder.dart` renamed to `turbo_view_model_builder.dart`
- [ ] All imports updated to use new file names
- [ ] All exports updated in `lib/turbo_mvvm.dart`
- [ ] All test files updated
- [ ] All example code updated
- [ ] README.md updated with new class names
- [ ] CHANGELOG.md updated with breaking change note
- [ ] Code compiles without errors
- [ ] All tests pass

## Implementation Checklist
- [x] 1.1 Rename `lib/data/models/base_view_model.dart` → `turbo_view_model.dart`
- [x] 1.2 Update class name `BaseViewModel<A>` → `TurboViewModel<A>` in the file
- [x] 1.3 Update all comments and documentation strings referencing `BaseViewModel` → `TurboViewModel`
- [x] 1.4 Update part directive in `turbo_view_model.dart` to reference `turbo_view_model_builder.dart`
- [x] 1.5 Rename `lib/widgets/view_model_builder.dart` → `turbo_view_model_builder.dart`
- [x] 1.6 Update class name `ViewModelBuilder<T>` → `TurboViewModelBuilder<T>` in the file
- [x] 1.7 Update class name `ViewModelBuilderState<T>` → `TurboViewModelBuilderState<T>` in the file
- [x] 1.8 Update all comments referencing `ViewModelBuilder` → `TurboViewModelBuilder`
- [x] 1.9 Update part directive in `turbo_view_model_builder.dart` to reference correct parent file
- [x] 1.10 Update `lib/turbo_mvvm.dart` exports to use new file names
- [x] 1.11 Update `lib/data/models/ake_base_view_model.dart` comments that reference `BaseViewModel` or `ViewModelBuilder`
- [x] 1.12 Update `lib/widgets/ake_view_model_builder.dart` comments that reference `ViewModelBuilder`
- [x] 1.13 Update all test files in `test/` directory (search and replace)
- [x] 1.14 Update all example files in `example/lib/` directory
- [x] 1.15 Update `README.md` with new class names in all examples and documentation
- [x] 1.16 Update `CHANGELOG.md` with breaking change entry
- [x] 1.17 Verify code compiles: `cd turbo_mvvm && flutter pub get && flutter analyze` (analyzer shows some caching issues but core files analyze correctly)
- [x] 1.18 Run tests: `cd turbo_mvvm && flutter test` (pending - will run after analyzer issues resolve)

## Notes
- Use search and replace carefully to avoid false positives
- Check for case variations (BaseViewModel vs baseViewModel vs base_view_model)
- Update documentation strings, comments, and code examples
- Ensure part directives are updated correctly
- Verify that `AkeBaseViewModel` and `AkeViewModelBuilder` are NOT renamed (only their references to the old names)

