##############
#   Build    #
##############

# Generate the site
# Minify, optimize, and compress

desc "build the site"
task :build do
  system "bundle exec jekyll build --incremental"
  system "bundle exec rake minify_html" #Minify our HTML
end

##############
#   Develop  #
##############

# Useful for development
# It watches for chagnes and updates when it finds them

desc "Watch the site and regenerate when it changes"
task :watch do
  system "bundle exec jekyll serve --watch"
end

##############
#   Deploy   #
##############

# Deploy the site
# Ping / Notify after site is deployed

desc "deploy the site"
task :deploy do
  #system "bundle exec deploy"
  system "bundle exec rake notify" #ping google/bing about our sitemap updates
end

##############
#   Notify   #
##############

# Ping Google and Yahoo to let them know you updated your site

site = "bsidessf.com"

desc 'Notify Google of the new sitemap'
task :sitemapgoogle do
  begin
    require 'net/http'
    require 'uri'
    puts '* Pinging Google about our sitemap'
    Net::HTTP.get('www.google.com', '/webmasters/tools/ping?sitemap=' + URI.escape('#{site}/sitemap.xml'))
  rescue LoadError
    puts '! Could not ping Google about our sitemap, because Net::HTTP or URI could not be found.'
  end
end

desc 'Notify Bing of the new sitemap'
task :sitemapbing do
  begin
    require 'net/http'
    require 'uri'
    puts '* Pinging Bing about our sitemap'
    Net::HTTP.get('www.bing.com', '/webmaster/ping.aspx?siteMap=' + URI.escape('#{site}/sitemap.xml'))
  rescue LoadError
    puts '! Could not ping Bing about our sitemap, because Net::HTTP or URI could not be found.'
  end
end

desc "Notify various services about new content"
task :notify => [:sitemapgoogle, :sitemapbing] do
end
