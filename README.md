Quick demo for http://stackoverflow.com/a/15765921/58876.

View changes in a working tree compared to a different branch.

Setup:
```bash
git clone https://github.com/jordan-brough/git-diff-test.git
cd git-diff-test
git checkout bar
# make a change:
echo 'line 3' >> foo
# stage the change:
git add foo
# make another change and don't stage it:
echo 'line 4' >> foo
```

Normal diff:
```bash
git diff -- foo
```
```diff
diff --git a/foo b/foo
index a92d664..9c2a709 100644
--- a/foo
+++ b/foo
@@ -1,3 +1,4 @@
 line 1
 line 2
 line 3
+line 4
```

Diff against master:
```bash
git diff master -- foo
```
```diff
diff --git a/foo b/foo
index 89b24ec..9c2a709 100644
--- a/foo
+++ b/foo
@@ -1 +1,4 @@
 line 1
+line 2
+line 3
+line 4
```

Diff against master restricted to staged changes:
```bash
git diff --cached master -- foo
```
```diff
diff --git a/foo b/foo
index 89b24ec..a92d664 100644
--- a/foo
+++ b/foo
@@ -1 +1,3 @@
 line 1
+line 2
+line 3
```
