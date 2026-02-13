# Setting Up Local Jekyll Server

## Quick Setup for Windows

### Step 1: Install Ruby
1. Download RubyInstaller from: https://rubyinstaller.org/downloads/
2. Install Ruby+Devkit (recommended version: Ruby 3.2.x or 3.3.x)
3. During installation, check "Add Ruby executables to your PATH"
4. After installation, run the `ridk install` command when prompted (for native extensions)

### Step 2: Install Jekyll and Bundler
Open a new terminal and run:
```powershell
gem install jekyll bundler
```

### Step 3: Create a Gemfile (if needed)
If there's no Gemfile, create one with:
```ruby
source "https://rubygems.org"
gem "jekyll", "~> 4.3"
```

### Step 4: Install dependencies
```powershell
bundle install
```

### Step 5: Run the local server
```powershell
bundle exec jekyll serve
```

Or if you don't use Bundler:
```powershell
jekyll serve
```

The site will be available at: **http://localhost:4000**

---

## Alternative: Using Docker (if you have Docker installed)

```powershell
docker run --rm -it -v "${PWD}:/srv/jekyll" -p 4000:4000 jekyll/jekyll:latest jekyll serve
```

---

## Alternative: Using GitHub Codespaces or WSL

If you have WSL (Windows Subsystem for Linux) installed, you can use Linux commands:
```bash
sudo apt-get install ruby-full build-essential zlib1g-dev
gem install jekyll bundler
bundle install
bundle exec jekyll serve
```
