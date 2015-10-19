MASTER_YAML = File.join('/etc/puppet', 'Puppetfile.yaml')
USER_YAML   = File.join(File.dirname(__FILE__), 'Environment.yaml')

require 'yaml'
require 'deep_merge'

master_data = {}
user_data = {}

if File.readable?(MASTER_YAML)
  master_data = YAML.load_file(MASTER_YAML)
end

if File.readable?(USER_YAML)
  user_data = YAML.load_file(USER_YAML)
end

data = user_data.deep_merge(master_data)

data['modules'].each_pair do |modulename, moduledata|
  mod modulename, :git => moduledata['git'],
                  :branch => moduledata['branch']
end
