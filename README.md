# react-xarrows-issue-118-repo

https://github.com/Eliav2/react-xarrows/issues/118

To reproduce:

1. Run `npm run build`
2. Run `npm run analyze`
3. Look at HTML file that opens (keep this open for step 7)
4. Uncomment the 2 lines that are commented out in `App.tsx`
5. Run `npm run build`
6. Run `npm run analyze`
7. Look at HTML file that opens (and compare with the file from step 3)

As shown by the two generated HTML files, the 2nd version that imports `Xarrow` results in `69.95KB` of JS added to the production bundle via `lodash/lodash.js`. So this proves that https://bundlephobia.com/package/react-xarrows@2.0.2 is correct, that all (or at least a large and unnecessary amount) of `lodash` is required to be bundled with `react-xarrows` (as the current way that `lodash` is used in `react-xarrows` doesn't allow the dead code to be tree shaken).
