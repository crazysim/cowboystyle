# A sample Guardfile
# More info at https://github.com/guard/guard#readme


guard 'compass' do
  watch(/^sass\/(.*)\.s[ac]ss/)
end

# Add files and commands to this file, like the example:
#   watch(%r{file/path}) { `command(s)` }
#
guard 'shell' do
    watch(/(.*).txt/) {|m| `tail #{m[0]}` }
    watch(%r{stylesheets/(day|night)\.css}) do
     `rake deploy`
    end
end

guard 'rake', :task => 'build' do
  watch(%r{^my_file.rb})
end
