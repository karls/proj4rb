require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "proj4rb"
    gem.summary = %Q{Ruby bindings for the Proj.4 Carthographic Projection library}
    gem.description = %Q{Proj4rb is a ruby binding for the Proj.4 Carthographic Projection library, that supports conversions between a very large number of geographic coordinate systems and datums.}
    gem.email = "guilhem.vellut@gmail.com"
    gem.homepage = "http://github.com/Caged/proj4rb"
    gem.authors = ["Guilhem Vellut"]
    gem.email = 'guilhem.vellut@gmail.com'
    gem.required_ruby_version = '>= 1.9'
    gem.requirements << 'Proj.4 C library'
    gem.extensions = ['ext/extconf.rb']
    gem.files = Dir.glob("{data,ext,example,test,lib}/**/*") + %w(LICENSE README.rdoc ChangeLog TODO Rakefile)    
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.pattern = 'test/**/test_*.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end

task :test => :check_dependencies

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "proj4rb #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
  rdoc.options.concat ['--main',  'README.rdoc']
end
