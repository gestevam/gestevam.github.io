# gestevam.github.io


### Technologies this website uses:
   <p>Jekyll
     <br>
     Github Pages </p>

### To make a similar site:

 1. Check Gemfile plugins using the bundler tool - make sure they work on you local system
     ```
     sudo gem install bundler
     bundle install
     bundle exec jekyll serve
     ```

 2. Create a conda environment - locally test and host:
    ```
     conda create -n jekyll -c conda-forge rb-jekyll
     conda activate jekyll
     bundle install
     bundle exec jekyll serve
    ```

#### **This website was built with inspiration and modifications from [open source code](https://github.com/fraser-lab/fraser-lab.github.io) and its accompanying [post](https://fraserlab.com/2020/05/03/Clone-this-website/)**
