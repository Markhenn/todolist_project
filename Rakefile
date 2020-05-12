require "rake/testtask"
require "bundler/gem_tasks"
require "find"

desc 'Say hello'
task :hello do
  puts "Hello there. This is the 'hello' task."
end

desc 'Run tests'
task :default => :test

Rake::TestTask.new(:test) do |t|
  t.libs << "test"
  t.libs << "lib"
  t.test_files = FileList['test/**/*_test.rb']
end

desc 'List all visible files'
task :list do
  Find.find(Dir.pwd) do |path|
    if FileTest.directory?(path)
      if File.basename(path).start_with?('.')
        Find.prune
      else
        next
      end
    else
      unless File.basename(path).start_with?('.')
        puts path
      end
    end
  end
end

desc 'Display inventory of all files'
task :inventory do
  Find.find('.') do |name|
    next if name.include?('/.') # Excludes files and directories with . names
    puts name if File.file?(name)
  end
end
