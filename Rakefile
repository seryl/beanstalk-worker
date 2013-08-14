# encoding: utf-8

require 'rubygems'
require 'bundler'
require './lib/beanstalk-worker.rb'

begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end
require 'rake'

require 'jeweler'
Jeweler::Tasks.new do |gem|
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "beanstalk-worker"
  gem.version = BeanStalk::Worker::VERSION
  gem.homepage = "http://github.com/aia/beanstalk-worker"
  gem.license = "MIT"
  gem.summary = %Q{Beanstalkd Worker base class}
  gem.description = %Q{Beanstalkd Worker base class}
  gem.email = ["artem@veremey.net", "joshtoft@gmail.com"]
  gem.authors = ["Artem Veremey", "Josh Toft"]
  # dependencies defined in Gemfile
end
Jeweler::RubygemsDotOrgTasks.new

require 'rspec/core'
require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new(:spec) do |spec|
  spec.pattern = FileList['spec/**/*_spec.rb']
end

if RUBY_VERSION =~ /^1\.9/
  desc "Code coverage detail"
  task :simplecov do
    ENV['COVERAGE'] = "true"
    Rake::Task['spec'].execute
  end
else
  RSpec::Core::RakeTask.new(:rcov) do |spec|
    spec.pattern = 'spec/**/*_spec.rb'
    spec.rcov = true
  end
end

require 'cucumber/rake/task'
Cucumber::Rake::Task.new(:features)

task :default => :spec

require 'yard'
YARD::Rake::YardocTask.new
