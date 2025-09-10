# Button Quick Reference

## Quick Start

```jsx
import { Button } from './components/Button';

<Button variant="primary" onClick={handleClick}>
  Click Me
</Button>
```

## Common Patterns

### Form Buttons
```jsx
// Submit
<Button type="submit" loading={isSubmitting}>
  {isSubmitting ? 'Submitting...' : 'Submit'}
</Button>

// Cancel
<Button variant="secondary" onClick={onCancel}>
  Cancel
</Button>
```

### Action Buttons
```jsx
// Save
<Button variant="primary" onClick={handleSave}>
  Save Changes
</Button>

// Delete
<Button variant="danger" onClick={handleDelete}>
  Delete
</Button>
```

### Size Variations
```jsx
<Button size="small">Small</Button>
<Button size="medium">Medium</Button>
<Button size="large">Large</Button>
```

## Props Cheat Sheet

| Prop | Values | Default |
|------|--------|---------|
| `variant` | `primary`, `secondary`, `tertiary`, `danger` | `primary` |
| `size` | `small`, `medium`, `large` | `medium` |
| `type` | `button`, `submit`, `reset` | `button` |
| `disabled` | `true`, `false` | `false` |
| `loading` | `true`, `false` | `false` |
| `fullWidth` | `true`, `false` | `false` |

## Accessibility Quick Tips

- Always use descriptive text
- Add `ariaLabel` for context when needed
- Ensure 44px minimum touch target
- Support keyboard navigation (Enter/Space)

For complete documentation, see [button.md](./button.md).