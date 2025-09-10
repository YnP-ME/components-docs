# Button Component

## Overview

The Button component is a fundamental UI element that enables user interaction through clicks, taps, or keyboard activation. It provides a consistent and accessible way to trigger actions, submit forms, navigate between pages, or perform any user-initiated operation.

## Purpose

- **Action Trigger**: Initiate actions like form submission, data processing, or navigation
- **User Interaction**: Provide clear interactive elements with visual feedback
- **Accessibility**: Ensure keyboard navigation and screen reader compatibility
- **Consistency**: Maintain uniform styling and behavior across the application

## Component API

### Props

| Prop | Type | Default | Required | Description |
|------|------|---------|----------|-------------|
| `variant` | `'primary' \| 'secondary' \| 'tertiary' \| 'danger'` | `'primary'` | No | Visual style variant of the button |
| `size` | `'small' \| 'medium' \| 'large'` | `'medium'` | No | Size of the button |
| `disabled` | `boolean` | `false` | No | Whether the button is disabled |
| `loading` | `boolean` | `false` | No | Shows loading state with spinner |
| `fullWidth` | `boolean` | `false` | No | Makes button take full width of container |
| `type` | `'button' \| 'submit' \| 'reset'` | `'button'` | No | HTML button type attribute |
| `onClick` | `(event: MouseEvent) => void` | `undefined` | No | Click event handler |
| `children` | `ReactNode` | `undefined` | Yes | Button content (text, icons, etc.) |
| `className` | `string` | `undefined` | No | Additional CSS classes |
| `id` | `string` | `undefined` | No | HTML id attribute |
| `ariaLabel` | `string` | `undefined` | No | Accessibility label for screen readers |

### Variants

#### Primary Button
- **Use Case**: Main actions, call-to-action buttons
- **Styling**: Filled background with brand color, high contrast
- **Example**: Submit forms, confirm actions, primary navigation

#### Secondary Button  
- **Use Case**: Secondary actions, alternative options
- **Styling**: Outlined style or subtle background
- **Example**: Cancel actions, alternative choices

#### Tertiary Button
- **Use Case**: Less prominent actions, supplementary controls
- **Styling**: Text-only or minimal styling
- **Example**: Links, minor actions, "Learn more" buttons

#### Danger Button
- **Use Case**: Destructive or critical actions
- **Styling**: Red/error color scheme
- **Example**: Delete, remove, destructive confirmations

### Sizes

- **Small**: Compact buttons for tight spaces or secondary actions
- **Medium**: Standard size for most use cases
- **Large**: Prominent buttons for important actions or mobile interfaces

## Usage Examples

### Basic Usage

```jsx
import { Button } from './components/Button';

// Primary button
<Button onClick={handleSubmit}>
  Submit Form
</Button>

// Secondary button with custom styling
<Button 
  variant="secondary" 
  size="large" 
  className="custom-button"
>
  Cancel
</Button>
```

### Form Integration

```jsx
// Submit button
<Button 
  type="submit" 
  variant="primary"
  loading={isSubmitting}
  disabled={!isFormValid}
>
  {isSubmitting ? 'Submitting...' : 'Submit'}
</Button>

// Reset button
<Button 
  type="reset" 
  variant="tertiary"
  onClick={handleReset}
>
  Reset Form
</Button>
```

### Destructive Actions

```jsx
<Button 
  variant="danger"
  onClick={handleDelete}
  ariaLabel="Delete item permanently"
>
  Delete Item
</Button>
```

### Loading State

```jsx
<Button 
  loading={isLoading}
  disabled={isLoading}
  onClick={handleAsyncAction}
>
  {isLoading ? 'Processing...' : 'Process Data'}
</Button>
```

### Full Width Layout

```jsx
<Button 
  fullWidth
  variant="primary"
  size="large"
>
  Continue
</Button>
```

## Styling and Theming

### CSS Custom Properties

The button component uses CSS custom properties for consistent theming:

```css
.button {
  /* Colors */
  --button-primary-bg: #007bff;
  --button-primary-text: #ffffff;
  --button-primary-border: #007bff;
  
  /* Spacing */
  --button-padding-sm: 0.5rem 1rem;
  --button-padding-md: 0.75rem 1.5rem;
  --button-padding-lg: 1rem 2rem;
  
  /* Typography */
  --button-font-size-sm: 0.875rem;
  --button-font-size-md: 1rem;
  --button-font-size-lg: 1.125rem;
  
  /* Border radius */
  --button-border-radius: 0.375rem;
  
  /* Transitions */
  --button-transition: all 0.2s ease-in-out;
}
```

### State Styles

```css
/* Hover state */
.button:hover:not(:disabled) {
  transform: translateY(-1px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

/* Active state */
.button:active {
  transform: translateY(0);
}

/* Focus state */
.button:focus {
  outline: 2px solid var(--focus-color);
  outline-offset: 2px;
}

/* Disabled state */
.button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
  pointer-events: none;
}
```

### Dark Mode Support

```css
@media (prefers-color-scheme: dark) {
  .button {
    --button-primary-bg: #0d6efd;
    --button-secondary-border: #6c757d;
    /* ... other dark mode overrides */
  }
}
```

## Accessibility

### WCAG Compliance

The button component follows WCAG 2.1 AA guidelines:

- **Contrast Ratio**: Minimum 4.5:1 for text, 3:1 for non-text elements
- **Touch Target Size**: Minimum 44px x 44px for touch interfaces
- **Focus Management**: Clear focus indicators and logical tab order

### Keyboard Navigation

- **Enter**: Activates the button
- **Space**: Activates the button  
- **Tab**: Moves focus to next focusable element
- **Shift + Tab**: Moves focus to previous focusable element

### Screen Reader Support

```jsx
// Descriptive labels
<Button ariaLabel="Save document and close editor">
  Save
</Button>

// State announcements
<Button 
  loading={isLoading}
  ariaLabel={isLoading ? 'Saving document...' : 'Save document'}
>
  {isLoading ? 'Saving...' : 'Save'}
</Button>
```

### ARIA Attributes

- `aria-label`: Provides accessible name when button text is insufficient
- `aria-disabled`: Indicates disabled state to assistive technologies
- `aria-pressed`: For toggle buttons (if applicable)
- `aria-expanded`: For buttons that control collapsible content

## Best Practices

### Do's ✅

1. **Clear Labels**: Use descriptive, action-oriented text
2. **Consistent Placement**: Follow established patterns for button positioning
3. **Visual Hierarchy**: Use variants appropriately to show importance
4. **Loading States**: Provide feedback during async operations
5. **Accessibility**: Always consider keyboard and screen reader users
6. **Touch Targets**: Ensure buttons are large enough for touch interaction

### Don'ts ❌

1. **Ambiguous Text**: Avoid generic labels like "Click here" or "Button"
2. **Too Many Primary**: Don't have multiple primary buttons in the same context
3. **Inconsistent Styling**: Maintain consistent button styles across the application
4. **Poor Contrast**: Ensure sufficient color contrast for readability
5. **Disabled Without Explanation**: Provide context for why a button is disabled

### Example Implementations

#### Good Implementation
```jsx
<div className="form-actions">
  <Button 
    type="submit"
    variant="primary"
    loading={isSubmitting}
    disabled={!isFormValid}
    ariaLabel="Submit contact form"
  >
    Send Message
  </Button>
  
  <Button 
    type="button"
    variant="secondary"
    onClick={handleCancel}
  >
    Cancel
  </Button>
</div>
```

#### Avoid This
```jsx
// Poor example - avoid this
<div>
  <Button variant="primary">Click</Button>
  <Button variant="primary">Submit</Button>
  <Button disabled>Button</Button>
</div>
```

## Integration Guidelines

### Testing

```jsx
// Unit test example
import { render, fireEvent, screen } from '@testing-library/react';
import { Button } from './Button';

test('calls onClick handler when clicked', () => {
  const handleClick = jest.fn();
  render(<Button onClick={handleClick}>Click me</Button>);
  
  fireEvent.click(screen.getByRole('button'));
  expect(handleClick).toHaveBeenCalledTimes(1);
});

test('shows loading state correctly', () => {
  render(<Button loading>Submit</Button>);
  expect(screen.getByRole('button')).toBeDisabled();
});
```

### Performance Considerations

- Use React.memo for buttons that don't need frequent re-renders
- Avoid creating new function references in render (use useCallback)
- Consider button icon optimizations for better loading performance

### Browser Support

- **Modern Browsers**: Full feature support
- **IE11**: Basic functionality with graceful degradation
- **Mobile**: Touch-optimized with appropriate sizing
- **Screen Readers**: Full compatibility with NVDA, JAWS, VoiceOver

## Related Components

- **IconButton**: For icon-only buttons
- **ButtonGroup**: For grouping related buttons
- **FloatingActionButton**: For primary actions in mobile interfaces
- **ToggleButton**: For state-based interactions

---

*This documentation is part of the Custom UI Component Library. For questions or contributions, please refer to the main documentation or contact the development team.*