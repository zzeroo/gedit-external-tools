

desc "Installs the tools"
task :install do
  Dir.glob("#{File.join(File.dirname(__FILE__),'external-tools')}/*") do |file|
    puts "link file: #{file} in ~/.gnome2/gedit/tools"
    system("ln -s #{file} ~/.gnome2/gedit/tools")
  end
end

task :default => :install
