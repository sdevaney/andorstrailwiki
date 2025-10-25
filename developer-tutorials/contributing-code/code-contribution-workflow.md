---
description: This guide explains how to contribute code to the Andor's Trail project.
---

# Code Contribution Workflow

### Overview <a href="#overview" id="overview"></a>

Andor's Trail uses GitHub for version control and collaboration. The contribution workflow follows a fork-and-pull-request model.

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

* Git is installed and configured.
* GitHub account.
* Development environment set up (see Development Environment Setup).
* Understanding of Java and Android development.
* Familiarity with the Andor's Trail codebase.

### Step 1: Fork the Repository <a href="#step-1-fork-the-repository" id="step-1-fork-the-repository"></a>

1. Visit [https://github.com/AndorsTrailRelease/andors-trail](https://github.com/AndorsTrailRelease/andors-trail).
2. Click the "Fork" button in the top-right corner.
3. Select your account (you now have your own copy of the repository).
4. Note the URL of your fork: `https://github.com/YOUR_USERNAME/andors-trail`

### Step 2: Clone Your Fork <a href="#step-2-clone-your-fork" id="step-2-clone-your-fork"></a>

```bash
bash# Clone your fork
git clone https://github.com/YOUR_USERNAME/andors-trail.git
cd andors-trail

# Add upstream remote (the original repository)
git remote add upstream https://github.com/AndorsTrailRelease/andors-trail.git

# Verify remotes
git remote -v
# Should show:
# origin  → your fork
# upstream → original repository
```

### Step 3: Create a Feature Branch <a href="#step-3-create-a-feature-branch" id="step-3-create-a-feature-branch"></a>

Always create a new branch for your work:

```bash
bash# Update master with latest changes
git checkout master
git pull upstream master

# Create feature branch
git checkout -b feature/description-of-change

# Examples:
# git checkout -b fix/npc-dialogue-bug
# git checkout -b feature/add-new-skill
# git checkout -b improvement/optimize-combat-calculation
```

### Branch Naming Conventions <a href="#branch-naming-conventions" id="branch-naming-conventions"></a>

Use prefixes to categorize your branch:

* `fix/` - Bug fixes
* `feature/` - New features
* `improvement/` - Code improvements or refactoring
* `docs/` - Documentation updates
* `test/` - Test additions or improvements

Follow with a descriptive name using hyphens (not spaces):

* `fix/combat-hit-chance-calculation`
* `feature/new-actor-condition`
* `improvement/reduce-memory-usage`

### Step 4: Make Changes <a href="#step-4-make-changes" id="step-4-make-changes"></a>

1. Edit files in your IDE (Android Studio).
2. Follow the coding style guidelines (see below).
3. Build and test your changes.

### Coding Style Guidelines

### Java Code Style

```java
java// Class names: PascalCase
public class PlayerInventory {

    // Method names: camelCase
    public void addItem(Item item) {
        // Constant names: UPPER_SNAKE_CASE
        final int MAX_ITEMS = 100;
        
        // Variable names: camelCase
        int itemCount = items.size();
        
        // Indentation: 4 spaces
        if (itemCount < MAX_ITEMS) {
            items.add(item);
        }
    }
    
    // Javadoc comments for public methods
    /**
     * Removes an item from the player's inventory.
     *
     * @param itemId The ID of the item to remove
     * @return true if item was found and removed, false otherwise
     */
    public boolean removeItem(String itemId) {
        return items.removeIf(item -> item.getId().equals(itemId));
    }
}
```

### Formatting Rules

* Use 4 spaces for indentation (not tabs).
* Maximum line length: 100 characters.
* Add blank lines between methods.
* Add spaces around operators: `a + b`, not `a+b`
* Open braces on same line: `if (condition) {` not `if (condition)\n{`

### Comments

```java
java// Single-line comments for code explanation
int result = calculate(x, y); // Calculate result

/**
 * Multi-line comments (Javadoc) for public methods
 * describing purpose, parameters, and return value
 */
public int calculate(int x, int y) {
    // TODO: Add validation
    // FIXME: Handle edge case
    return x + y;
}
```

### Step 5: Test Your Changes <a href="#step-5-test-your-changes" id="step-5-test-your-changes"></a>

### Build the Project

```bash
bash./gradlew clean build
```

### Run Tests

```bash
bash# Run all tests
./gradlew test

# Run specific test
./gradlew test --tests com.gpl.rpg.AndorsTrail.SomeTest

# Run with coverage
./gradlew test jacocoTestReport
```

### Test on Device/Emulator

1. Open Android Studio.
2. Click Run → Run 'AndorsTrail'.
3. Select an emulator or device.
4. Verify your changes work as expected.

### Manual Testing

* Test the specific feature you modified.
* Test edge cases and error conditions.
* Verify no regressions in other areas.
* Document your testing in the PR description.

### Step 6: Commit Changes <a href="#step-6-commit-changes" id="step-6-commit-changes"></a>

Use clear, descriptive commit messages:

```bash
bash# Stage files
git add src/com/gpl/rpg/AndorsTrail/SomeFile.java
git add test/com/gpl/rpg/AndorsTrail/SomeFileTest.java

# Commit with message
git commit -m "Fix combat hit chance calculation formula

- Updated ATAN formula to match specification
- Added edge case handling for zero values
- Updated related unit tests
- Fixes #123"
```

### Commit Message Format

```
text<type>: <subject>

<body>

<footer>
```

**Type:**

* `fix:` - Bug fix
* `feature:` - New feature
* `refactor:` - Code refactoring
* `test:` - Test additions
* `docs:` - Documentation

**Subject:**

* Use imperative mood ("fix", not "fixed").
* Don't capitalize the first letter.
* No period at the end.
* Maximum 50 characters.

**Body:**

* Explain what and why, not how.
* Wrap at 72 characters.
* Reference issue numbers: `Fixes #123`, `Closes #456`

**Example:**

```
textfix: correct player health calculation

The health calculation was using integer division instead of
proper rounding, causing incorrect damage calculations in edge
cases. Updated to use Math.round() for proper rounding.

Fixes #189
```

### Step 7: Keep Your Branch Updated <a href="#step-7-keep-your-branch-updated" id="step-7-keep-your-branch-updated"></a>

Before submitting, sync with upstream:

```bash
bash# Fetch latest changes
git fetch upstream

# Rebase on master
git rebase upstream/master

# If there are conflicts, resolve them:
# 1. Edit conflicted files
# 2. Mark as resolved: git add <file>
# 3. Continue rebase: git rebase --continue
```

Alternatively, merge if rebase is complex:

```bash
bashgit merge upstream/master
```

### Step 8: Push to Your Fork <a href="#step-8-push-to-your-fork" id="step-8-push-to-your-fork"></a>

```bash
bash# Push your branch
git push origin feature/description-of-change

# To force update (after rebase)
git push origin feature/description-of-change --force
```

### Step 9: Create a Pull Request <a href="#step-9-create-a-pull-request" id="step-9-create-a-pull-request"></a>

1. Visit your fork on GitHub,
2. Click "Compare & pull request" button,
3. Fill in the PR form:

### PR Title

Clear, concise description:

* "Fix combat hit chance calculation",
* "Add new actor condition: Petrified",
* "Optimize memory usage in map loading",

### PR Description

```
text## Description
Brief description of what this PR does.

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Improvement
- [ ] Documentation

## Changes Made
- Change 1
- Change 2
- Change 3

## Testing
Describe how you tested the changes:
- Tested on emulator (API 25)
- Tested on device (Pixel 4, Android 11)
- All unit tests pass

## Closes
Fixes #123

## Additional Notes
Any additional context.
```

4. Request reviewers (if known),
5. Click "Create pull request",

### Step 10: Code Review <a href="#step-10-code-review" id="step-10-code-review"></a>

Reviewers will:

* Examine your code,
* Check for bugs and issues,
* Verify adherence to style guidelines,
* Request changes if needed,

### Responding to Review Comments

1. Don't be defensive - feedback improves code quality,
2. Make requested changes in new commits,
3. Push changes to the same branch (automatically updates PR),
4. Reply to comments explaining changes,
5. Click "Resolve conversation" when addressed,

### Addressing Review Feedback

```bash
bash# Make requested changes
# Edit files...

# Commit changes
git commit -m "Address review feedback

- Improved variable naming
- Added error handling
- Updated documentation"

# Push to branch
git push origin feature/description-of-change
```

### Step 11: Merge <a href="#step-11-merge" id="step-11-merge"></a>

Once approved:

1. The maintainers will merge your PR.
2. Your branch can be deleted.
3. Changes are now in the main repository.

### After Merge <a href="#after-merge" id="after-merge"></a>

```bash
bash# Update local master
git checkout master
git pull upstream master

# Delete local feature branch
git branch -d feature/description-of-change

# Delete remote feature branch (if not auto-deleted)
git push origin --delete feature/description-of-change
```

### Coding Standards <a href="#coding-standards" id="coding-standards"></a>

### Javadoc Requirements

* All public classes and methods must have Javadoc.
* Describe purpose, parameters, return value, and exceptions.
* Include example usage for complex methods.

```java
java/**
 * Calculates player attack chance against a target.
 *
 * Formula: AC = 50 + (2/π) * arctan((AC - 50) / 40)
 *
 * @param playerAC Player's attack chance (0-100)
 * @param targetBC Target's block chance (0-100)
 * @return Effective attack chance (0-100)
 */
public int calculateHitChance(int playerAC, int targetBC) {
    // Implementation
}
```

### Error Handling

* Check for null values.
* Handle expected exceptions.
* Use meaningful error messages.
* Log errors appropriately.

```java
javapublic Item getItem(String itemId) {
    if (itemId == null || itemId.isEmpty()) {
        throw new IllegalArgumentException("Item ID cannot be null or empty");
    }
    
    Item item = items.get(itemId);
    if (item == null) {
        Log.w(TAG, "Item not found: " + itemId);
        return null;
    }
    
    return item;
}
```

### Testing Requirements

* Write unit tests for new functionality.
* Maintain or improve code coverage.
* Test edge cases and error conditions.

```java
javapublic class PlayerInventoryTest {
    
    @Test
    public void testAddItem() {
        PlayerInventory inventory = new PlayerInventory();
        Item item = new Item("sword");
        
        inventory.addItem(item);
        
        assertTrue(inventory.contains("sword"));
    }
    
    @Test
    public void testAddItemWithNull() {
        PlayerInventory inventory = new PlayerInventory();
        
        assertThrows(NullPointerException.class, 
            () -> inventory.addItem(null));
    }
}
```

### Common Issues <a href="#common-issues" id="common-issues"></a>

### PR Not Updating After Changes

```bash
bash# Ensure you're pushing to the same branch
git push origin feature/description-of-change

# If force push was needed
git push origin feature/description-of-change --force
```

### Merge Conflicts

```bash
bash# Update your branch
git fetch upstream
git rebase upstream/master

# Resolve conflicts in editor, then:
git add .
git rebase --continue
git push origin feature/description-of-change --force
```

### CI/CD Pipeline Failed

Check the build logs:

1. View logs in GitHub (GitHub Actions tab).
2. Fix issues indicated by failures.
3. Commit and push changes.
4. CI automatically reruns.

### Review Checklist <a href="#review-checklist" id="review-checklist"></a>

Before submitting, verify:

* [ ] &#x20;A branch was created from the latest master.
* [ ] &#x20;Code follows style guidelines.
* [ ] &#x20;All tests pass locally.
* [ ] &#x20;No unnecessary comments or debug code.
* [ ] &#x20;Commit messages are clear.
* [ ] &#x20;PR description is complete.
* [ ] &#x20;Related issues are referenced.
* [ ] &#x20;Documentation updated (if needed).
* [ ] &#x20;No large unrelated changes.

### Resources <a href="#resources" id="resources"></a>

* [GitHub Collaboration Guide](https://docs.github.com/en/pull-requests)
* [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)
* [Android Development Guidelines](https://developer.android.com/develop)
* [Andor's Trail Forums](https://andorstrail.com/)
* [Andor's Trail GitHub Issues](https://github.com/AndorsTrailRelease/andors-trail/issues)

### Getting Help <a href="#getting-help" id="getting-help"></a>

* Check existing issues and discussions.
* Ask on Andor's Trail forums.
* Comment on related GitHub issues.
* Request help from maintainers.
