desc "Deploy _site/"
task :deploy do
  puts "\n## Rebuild"
  system('jekyll build')
  puts "\n## Staging modified files"
  status = system("git add -A")
  puts status ? "Success" : "Failed"
  puts "\n## Committing a site build at #{Time.now.utc}"
  message = "Build site at #{Time.now.utc}"
  status = system("git commit -m \"#{message}\"")
  puts status ? "Success" : "Failed"
  puts "\n## Pulling latest from remote"
  status = system("git pull origin gh-pages")
  puts status ? "Success" : "Failed"
  message = "Merge #{Time.now.utc}"
  status = system("git commit -a -m \"#{message}\"")
  puts "\n## Pushing commits to remote"
  status = system("git push origin gh-pages")
  puts status ? "Success" : "Failed"
end

desc "Work _site/"
task :work do
  puts "\n## working locally..."
  system('jekyll build')
  system("jekyll serve --safe --watch --baseurl=")
end