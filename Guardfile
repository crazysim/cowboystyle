# A sample Guardfile
# More info at https://github.com/guard/guard#readme


# guard 'compass' do
  # watch(%r{sass/(.*)\.s[ac]ss/})
# end

# Add files and commands to this file, like the example:
#   watch(%r{file/path}) { `command(s)` }
#
guard 'shell' do
    watch(/(.*).txt/) {|m| `tail #{m[0]}` }
    watch(%r{sass/(.*)\.s[ac]ss/}) do
     `rake deploy`
    end
end
