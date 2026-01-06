# Spec: MVVM Pattern

## ADDED Requirements

### Requirement: TurboViewModel Base Class
The `turbo_mvvm` package MUST provide a `TurboViewModel<A>` abstract class that serves as the base class for all ViewModels, where `A` is the type of arguments passed to the ViewModel.

#### Scenario: Developer creates a ViewModel
- **WHEN** a developer extends `TurboViewModel<String>` for a ViewModel that accepts string arguments
- **THEN** the ViewModel inherits lifecycle management (`initialise()`, `dispose()`)
- **AND** the ViewModel can access arguments via the `arguments` property
- **AND** the ViewModel can check mount status via `isMounted`
- **AND** the ViewModel can access `BuildContext` safely via `context`

#### Scenario: ViewModel initializes with arguments
- **WHEN** a `TurboViewModel` is created with arguments via `TurboViewModelBuilder`
- **THEN** the `arguments` property contains the provided arguments
- **AND** the `initialise()` method is called automatically
- **AND** the `isInitialised` notifier reflects the initialization state

#### Scenario: ViewModel disposes resources
- **WHEN** a `TurboViewModel` is removed from the widget tree
- **THEN** the `dispose()` method is called automatically
- **AND** all resources are cleaned up (disposableBuildContext, mounted callback, etc.)

### Requirement: TurboViewModelBuilder Widget
The `turbo_mvvm` package MUST provide a `TurboViewModelBuilder<T>` widget that builds and provides a `TurboViewModel` to the widget tree, where `T` extends `TurboViewModel`.

#### Scenario: Developer uses TurboViewModelBuilder
- **WHEN** a developer wraps their widget tree with `TurboViewModelBuilder<MyViewModel>`
- **THEN** the ViewModel is created via the `viewModelBuilder` callback
- **AND** arguments are provided via the `argumentBuilder` callback
- **AND** the ViewModel is automatically initialized
- **AND** the builder receives the ViewModel instance, initialization state, and context

#### Scenario: TurboViewModelBuilder rebuilds on state changes
- **WHEN** a `TurboViewModel` calls `rebuild()` or notifies listeners
- **THEN** the `TurboViewModelBuilder` rebuilds its child widgets
- **AND** the builder function receives the updated ViewModel state

#### Scenario: TurboViewModelBuilder handles disposal
- **WHEN** a `TurboViewModelBuilder` is removed from the widget tree
- **THEN** the ViewModel's `dispose()` method is called
- **AND** the `onDispose` callback is invoked if provided

### Requirement: TurboViewModelBuilderState
The `TurboViewModelBuilder` MUST have an associated `TurboViewModelBuilderState<T>` that manages the ViewModel lifecycle.

#### Scenario: State manages ViewModel lifecycle
- **WHEN** `TurboViewModelBuilderState` is initialized
- **THEN** it creates the ViewModel instance
- **AND** it sets up the disposable build context
- **AND** it sets the mounted callback
- **AND** it calls the ViewModel's `initialise()` method

#### Scenario: State provides ViewModel to widget tree
- **WHEN** `TurboViewModelBuilderState` builds
- **THEN** it provides the ViewModel via `ChangeNotifierProvider`
- **AND** it listens to the `isInitialised` notifier
- **AND** it rebuilds when the ViewModel notifies listeners (if reactive)

