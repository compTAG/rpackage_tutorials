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

