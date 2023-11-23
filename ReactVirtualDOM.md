## Traditional Approach (Without Virtual DOM):

1. **Data**
2. **Template**
3. Combine **data + template** to generate real DOM for display.
4. When **state changes**, repeat the process to generate a new real DOM and replace the original DOM.

**Drawbacks:**
- The first time generates a complete DOM fragment.
- The second time generates another complete DOM fragment.
- The second DOM replaces the first one, which is very performance-intensive.

---

## Traditional Approach with Manual DOM Update:

1. **Data**
2. **Template**
3. Combine **data + template** to generate real DOM for display.
4. When **state changes**, repeat the process to generate a new real DOM, but it doesn't replace the original DOM.
5. Compare the new DOM (`DocumentFragment`) with the original DOM to find differences.
6. Identify changes, e.g., in input elements.
7. Use only the new DOM's input elements to replace the corresponding elements in the old DOM.

**Drawbacks:**
- Performance improvement is not significant.

---

## Optimized Approach with Virtual DOM:

1. **State data**
2. **JSX template**
3. Combine **data + template** to generate real DOM for display.
   ```jsx
   <div id="abc"><span>Hello world</span></div>
