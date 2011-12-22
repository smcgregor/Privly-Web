load 'deploy' if respond_to?(:namespace) # cap2 differentiator

# Uncomment if you are using Rails' asset pipeline
# load 'deploy/assets'

Dir['vendor/gems/*/recipes/*.rb','vendor/plugins/*/recipes/*.rb'].each { |plugin| load(plugin) }

load 'config/deploy' # remove this line to skip loading any of the default tasks

namespace :deploy do

    after "deploy:update_code" do
      symlink_shared
    end
    
    desc "Create a symlink to domain, dev.domain or test.domain gmap_api_key.yml file"
    task :symlink_shared, :hosts => "#{domain}" do
        run "ln -s #{privly_shared_path}production.rb #{latest_release}/config/environments/production.rb"
        run "ln -s #{privly_shared_path}database.yml #{latest_release}/config/database.yml"
    end
end