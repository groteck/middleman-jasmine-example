require 'middleman/rack'
namespace :test do
  desc 'Run Jasmine-tests with PhantomJS and print result. Exit with code 1 or 0.'

  task :ci do
    server = Rack::Server.new(:app => Middleman.server)

    t = Thread.new do
      begin
        server.start
      rescue ChildProcess::TimeoutError
      end
      # # ignore bad exits
    end
    t.abort_on_exception = true

    system 'phantomjs phantom_runner.js http://localhost:8080/jasmine'

    t.kill
  end
end
