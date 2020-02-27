require 'rubygems'
Gem::manage_gems
require 'rake/gempackagetask'

spec = Gem::Specification.new do |s|
    s.platform  =   Gem::Platform::RUBY
    s.name      =   "git-ruby"
    s.version   =   "0.2.0"
    s.author    =   "Scott Chacon"
    s.email     =   "schacon@gmail.com"
    s.summary   =   "A pure ruby implementation of Git"
    s.files     =   FileList['lib/**/*', 'tests/**/*', 'doc/**/*'].to_a

    s.bindir = 'bin'
    s.executables << "gitr"
    s.homepage = "http://github/schacon/git-ruby"

    s.require_path  =   "lib"
    s.autorequire   =   "git-ruby"
    s.test_files = Dir.glob('tests/*.rb')
    s.has_rdoc  =   true
    s.extra_rdoc_files  =   ["README"]
end

Rake::GemPackageTask.new(spec) do |pkg|
    pkg.need_tar = true
end

task :default => "pkg/#{spec.name}-#{spec.version}.gem" do
    puts "generated latest version"
end

desc "Regenerate Documentation"
task :doc do |t|
 system('rdoc lib/ README --main README --inline-source')
end

desc "Upload Docs"
task :upload_docs do |t|
 system('rsync -rv --delete doc/ git-ruby.rubyforge.org:/var/www/gforge-projects/git-ruby')
end

desc "Run Unit Tests"
task :test do |t|
    require File.dirname(__FILE__) + '/tests/all_tests.rb'
end

