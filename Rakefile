require 'rubygems'
require 'rake'
require 'rake/testtask'
require 'rake/packagetask'
require 'rubygems/package_task'

desc 'Generates a dummy app for testing'
task :test_app do
  ENV['LIB_NAME'] = 'spree_paypal_express'
  Rake::Task['extension:test_app'].invoke
end

require 'rspec/core'
require 'rspec/core/rake_task'
require 'rspec-rerun'
require 'spree/testing_support/extension_rake'

RSpec::Core::RakeTask.new(:spec) do |t|
  t.fail_on_error = false
end

desc "Run RSpec with code coverage"
task :coverage do
  ENV['COVERAGE'] = 'true'
  Rake::Task["spec"].execute
end
task :default => 'rspec-rerun:spec'


Bundler::GemHelper.install_tasks

Rake::Task[:release].tap do |task|
  task.clear
  task.instance_variable_set :@arg_names, nil
end

desc "Build and release v#{SpreePayPalExpress::VERSION} to Gemfury"
task :release => :build do
  sh "curl -F package=@pkg/spree_paypal_express-#{SpreePayPalExpress::VERSION}.gem https://#{ENV.fetch('GEMFURY_TOKEN')}@push.fury.io/#{ENV.fetch('GEMFURY_USERNAME')}/"
  sh "git tag v#{SpreePayPalExpress::VERSION} -m 'Release #{SpreePayPalExpress::VERSION}'"
  sh "git push origin v#{SpreePayPalExpress::VERSION}"
end
