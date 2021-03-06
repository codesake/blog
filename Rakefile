require 'rubygems'
require 'optparse'
require 'yaml'

## -- Rsync Deploy config -- ##
# Be sure your public key is listed in your server's ~/.ssh/authorized_keys file
ssh_user       = "thesp0nge@goliath.armoredcode.com"
ssh_port       = "22"
document_root  =  "/var/www/dawn.codesake.com"
rsync_delete   = true
deploy_default = "rsync"
public_dir      = "_site"    # compiled site directory

deploy_dir      = "_site"
source_dir      = "_source"

css_dir         = "#{deploy_dir}/stylesheets"
sass_dir        = "#{source_dir}/_sass"
image_dir       = "#{source_dir}/images"

desc "Create a new post"
task :np do
  OptionParser.new.parse!
  ARGV.shift
  title = ARGV.join(' ')

  path = "_posts/#{Date.today}-#{title.downcase.gsub(/[^[:alnum:]]+/, '-')}.markdown"
  
  if File.exist?(path)
  	puts "[WARN] File exists - skipping create"
  else
    File.open(path, "w") do |file|
      file.puts YAML.dump({'layout' => 'post', 'published' => false, 'title' => title, 'categories'=>'article', 'tags'=>nil, 'image'=>{'feature'=>nil, 'credit'=>nil, 'creditlink'=>nil}})
      file.puts "---"
    end
  end
  puts "post created at: #{path}"

  exit 1
end

desc "Generate jekyll site"
task :generate do
  puts "## Generating Site with Jekyll"
  system "jekyll build"
  system "compass compile --css-dir #{css_dir} --sass-dir #{sass_dir}"
end

desc "Deploy website via rsync"
task :rsync do
  exclude = ""
  if File.exists?('./rsync-exclude')
    exclude = "--exclude-from '#{File.expand_path('./rsync-exclude')}'"
  end
  puts "## Deploying website via Rsync"
  system("rsync -avze 'ssh -p #{ssh_port}' #{exclude} #{"--delete" unless rsync_delete == false} #{deploy_dir}/ #{ssh_user}:#{document_root}")
end

