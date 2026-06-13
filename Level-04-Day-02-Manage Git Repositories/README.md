### ❤️ Level 04 - Day 02 - Manage Git Repositories

---

## 🧑‍💻 1: Create the Repository in Gitea UI

1. Open your browser and click the **Gitea UI** button on your environment's top bar.
2. Log in with the following credentials:
* **Username:** `max`
* **Password:** `Max_pass123`


3. Click the **`+`** icon in the top right corner and select **New Repository**.
4. Configure the repository:
* **Repository Name:** `story_blog`
* Keep the rest of the settings as default (do not initialize with a README if you want a clean import, though Gitea usually provides instructions if empty).


5. Click **Create Repository**.
6. **Note the Repository URL:** It will look something like `http://<gitea-server-ip>:<port>/max/story_blog.git`.

> 💡 *Tip: Take a screenshot of your newly created repository page in Gitea for your records/review.*

---

## 🧑‍💻 2: Clone the Repository on the Storage Server

1. Open your terminal and SSH into the storage server as `max`:
```bash
ssh max@<storage-server-ip>

```


*(Enter password `Max_pass123` when prompted)*
2. Ensure you are in your home directory:
```bash
cd /home/max

```


3. Clone the repository using the HTTP URL copied from Step 1:
```bash
git clone http://<gitea-server-ip>:<port>/max/story_blog.git

```


4. Move into the project directory:
```bash
cd story_blog

```



---

## 🧑‍💻 3: Add Existing Data & Push to `main`

1. Copy all files from `/usr/security` into your repository folder:
```bash
cp -r /usr/security/* .

```


2. Stage all the newly added files:
```bash
git add .

```


3. Commit the changes with the exact required message:
```bash
git commit -m "add stories"

```


4. Push the changes to the `main` branch:
```bash
git push origin main

```


*(If prompted, enter your Gitea username `max` and password `Max_pass123`)*

---

## 🧑‍💻 4: Create a New Branch

1. Create and switch to the new branch named `max_apps`:
```bash
git checkout -b max_apps

```



---

## 🧑‍💻 5: Fix the Typo and Push to `max_apps`

1. Copy the target file from `/tmp/stories/` into your repository:
```bash
cp /tmp/stories/story-index-max.txt .

```


2. Open the file to fix the typo (you can use `nano` or `sed`). Let's use `sed` for a quick, precise fix:
```bash
sed -i 's/Mooose/Mouse/g' story-index-max.txt

```


*(Alternatively, run `nano story-index-max.txt`, find `Mooose`, change it to `Mouse`, then press `Ctrl+O` and `Ctrl+X` to save and exit).*
3. Stage the modified file:
```bash
git add story-index-max.txt

```


4. Commit the fix with the exact required message:
```bash
git commit -m "typo fixed for Mooose"

```


5. Push the new branch and its commit to the Gitea server:
```bash
git push origin max_apps

```



---

### Verification Checklist

* [ ] Refresh your Gitea UI page. You should see the files from `/usr/security` in the `main` branch.
* [ ] Switch the branch dropdown in the Gitea UI to `max_apps`. You should see `story-index-max.txt` listed there.
* [ ] Click on `story-index-max.txt` on Gitea to verify that `Mooose` has successfully been updated to `Mouse`.
