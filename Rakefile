require 'circleci'
require 'logger'
@logger = Logger.new($stdout)

CircleCi.configure do |config|
  config.token = ENV['CIRCLECI_TOKEN']
end

task :default do
  begin
    @logger.info "Run nightly integration"
    res = CircleCi::Project.build_branch 'higanworks', 'knife-zero', 'integration_testedge'
    @logger.info res.code
    unless res.code == 201
      @logger.error "Maybe fail, it will notifies to some service."
    end
  rescue => e
    @logger.error e.class
    @logger.error e.message
  end
end
