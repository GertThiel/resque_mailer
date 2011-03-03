require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "resque_mailer"
    gem.summary = %Q{Rails plugin for sending asynchronous email with ActionMailer and Resque (resque-igo, MongoDB)}
    gem.description = %Q{Rails plugin for sending asynchronous email with ActionMailer and Resque (resque-igo, MongoDB)}
    gem.email = "GertThiel@gmx.net"
    gem.homepage = "https://github.com/GertThiel/resque_mailer"
    gem.authors = ["Gert Thiel", "Nick Plante", "Marcin Kulik"]
    gem.add_development_dependency "rspec", ">= 1.2.9"
    gem.add_development_dependency "resque-igo", "~> 1.12.8"
    gem.add_development_dependency "actionmailer", ">= 2.3.4"
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

begin
  require 'spec/rake/spectask'

  puts "Using RSpec 1.x / Rails 2.x"

  desc "Run specs for Rails 2.x"
  Spec::Rake::SpecTask.new(:spec) do |spec|
    spec.spec_files = FileList['spec/common_spec.rb', 'spec/rails2_spec.rb']
  end
rescue LoadError
  puts "RSpec 1.x unavailable"
end

begin
  require 'rspec/core'
  require 'rspec/core/rake_task'

  puts "Using RSpec 2.x / Rails 3.x"

  desc "Run specs for Rails 3.x"
  RSpec::Core::RakeTask.new(:spec) do |spec|
    spec.pattern = ["spec/common_spec.rb","spec/rails3_spec.rb"]
  end
rescue LoadError
  puts "RSpec 2.x unavailable"
end

task :default => :spec

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "resque_mailer #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
