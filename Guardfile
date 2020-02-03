# Gollum Guard
#
# - watches for *.md changes
# - amends to the sessions commit
# - livereload browser

guard 'livereload' do
  watch(/.+\.md$/) do |m|
    system %Q(git add -A)
    system %Q(git commit --amend -m "$(cat .guardstamp)")
    m[0]
  end

  # start the sessions git commit
  callback(:start_begin) do
    system %Q(echo $(date "+session: %Y-%m-%d %H:%M") > .guardstamp)
    system %Q(git add .guardstamp)
    system %Q(git commit -m "$(cat .guardstamp)")
  end
end