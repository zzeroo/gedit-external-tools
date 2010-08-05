
desc "Installs the tools"
task :install do
  @source_dir = File.join(File.dirname(__FILE__),'external-tools') 
  @target_dir = File.join(ENV['HOME'],'.gnome2/gedit/tools')
  replace_all = false

  Dir.chdir(@source_dir) 
  Dir["*"].each do |file|
    next if %w[].include? file

    if File.exist?(File.join(@target_dir,file))
      if replace_all
        replace(file)
      else
        print "overwrite #{File.join(@target_dir,file)}? [ynaq] "
        case $stdin.gets.chomp
        when 'a'
          replace_all = true
          replace(file)
        when 'y'
          replace(file)
        when 'q'
          exit
        else
          puts "skipping #{file}" 
        end
      end
    else
      linkin(file)
    end  
  end
end

def replace(file)
  system %Q{rm #{File.join(@target_dir,file)}}
  linkin(file)
end

def linkin(file)
  puts "link file: #{File.join(@source_dir,file)} in #{@target_dir}"
  system %Q{ln -s #{File.join(@source_dir,file)} #{@target_dir}}
end

task :default => :install
