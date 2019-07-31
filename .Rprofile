gen_blog <- function(input = c(".", list.dirs("_source")), output =
                     c(".", rep("rmd_posts/_posts", length(list.dirs("_source")))),
                     command = "bundle exec jekyll build", ...) {
  servr::jekyll(input = input, output = output, serve = FALSE,
                command = command, ...)
}

serve_blog <- function (input = c(".", list.dirs("_source")), output = c(".",
    rep("rmd_posts/_posts", length(list.dirs("_source")))),
    command = "bundle exec jekyll build", ...)
{
    servr::jekyll(input = input, output = output, serve = TRUE,
                  command = command, ...)
}

use_package <- function(p) {
  if (!is.element(as.character(p), utils::installed.packages()[, 1]))
    utils::install.packages(p, dep = TRUE)
library(p, character.only = TRUE)
}

r <- getOption("repos")
r["CRAN"] <- "http://cran.wustl.edu/"
options(repos = r)
rm(r)


#use_package('TDA')
#use_package('servr')
