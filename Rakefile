task :install do
  linkables = Dir.glob('*{.symlink}')

  linkables.each do |linkable|
    file = linkable.split('.symlink').last
    target = "#{ENV["HOME"]}/.#{file}"

    if File.exists?(target) || File.symlink?(target)
      puts "Backup existing file #{target} to #{target}.backup"
      `mv "#{target}" "#{target}.backup"`
    end
    `ln -s "$PWD/#{linkable}" "#{target}"`
  end

  `echo source "$PWD/*.bash" >> "$HOME/.bashrc"`
end

task :default => :install
