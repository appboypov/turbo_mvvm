# Design: Rename BaseViewModel to TurboViewModel in turbo_mvvm

## Context
The `turbo_mvvm` package uses "turbo" as a prefix in its name, but the core classes (`BaseViewModel`, `ViewModelBuilder`) don't follow this convention. This creates inconsistency and makes it harder to discover related functionality.

## Goals
- Align class names with package naming conventions
- Improve consistency within the package
- Ensure all references are updated comprehensively

## Non-Goals
- Renaming `AkeBaseViewModel` and `AkeViewModelBuilder` (user preference)
- Modifying functionality (pure rename operation)

## Decisions

### Decision: Complete Rename (No Deprecation Period)
**Rationale**: Since this is a monorepo with coordinated releases, we can perform a clean rename. All consuming packages will be updated simultaneously.

**Alternative Considered**: Gradual deprecation with warnings
- **Rejected**: Adds complexity and confusion. Better to do a clean break.

### Decision: Update File Names
**Rationale**: File names should match class names for consistency and discoverability.

**Files Affected**:
- `base_view_model.dart` → `turbo_view_model.dart`
- `view_model_builder.dart` → `turbo_view_model_builder.dart`

## Migration Strategy

1. Rename `BaseViewModel` → `TurboViewModel` in `turbo_mvvm`
2. Rename `ViewModelBuilder` → `TurboViewModelBuilder` in `turbo_mvvm`
3. Update file names and exports
4. Update all tests and examples
5. Update documentation

## Risks / Trade-offs

### Risk: Breaking Changes
**Impact**: High - All consuming code must be updated
**Mitigation**: Coordinate with consuming package updates

### Risk: Missed References
**Impact**: Medium - Could cause compilation errors
**Mitigation**: Comprehensive search and replace, thorough testing

## Testing Strategy

1. **Compile Check**: Ensure package compiles without errors
2. **Import Check**: Verify all imports resolve correctly
3. **Test Check**: Run all tests to ensure they pass
4. **Example Check**: Run example app to ensure it works

## Open Questions
None - requirements are clear and comprehensive.

