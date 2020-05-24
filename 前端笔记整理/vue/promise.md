- 1. 1.Promise是一个构造函数
  2. 2.在Promise上,有两个函数,resolve(成功的回调函数),reject(失败的回调函数)
  3. 3.在Promise构造函数的Prototype属性上,有一个.then()方法
  4. 4.如果Promise表示一个异步操作,每当我们new一个Promise的实例,这个实例,就表示一个具体的异步操作
  5. 5.既然Promise创建的实例,是一个异步操作,那么,这个异步操作的结果,只能有成功和失败两种状态,内部拿到操作的结果后,无法使用return将结果返回给调用者,这时候,只能使用回调函数的形式,来把结果返回,resolve() /      reject()
  6. 6.我们可以在new出来的Promise实例上,调用.then()方法,[预先]为这个Promise异步操作,指定成功(resolve)和失败(reject)的回调函数
  7. 7.每当new一个Promise实例的时候,就会立即执行这个异步操作中的代码,用函数包裹可控制按需执行
  8. 8.如果前面的Promise执行失败,不想终止后续的Promise操作,可以为每个Promise添加失败的回调函数;相反,需求一旦有错就不再继续执行的情况,可使用.catch()
  9. 9.all() / race()