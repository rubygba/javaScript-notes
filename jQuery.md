#jQuery学习笔记
将函数（function()）放入jQuery对象
`function someFunction() {
    // Do interesting things
}
$(someFunction)`
或
`$(function(){
    // Do interesting things
})`

Now, you can include your script in the <head> and it won't run until the DOM has been built and the elements that you want to manipulate are on the page.
