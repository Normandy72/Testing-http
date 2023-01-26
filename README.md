# Testing AngularJS Services and $http
### beforeEach Setup
```
var myService;
var $httpBackend;

beforeEach(function(){
    module('MyApp');

    inject(function($injector){
        myService = $injector.get('MyService');
        $httpBackend = $injector.get('$httpBackend');
    });
});
```
`$injector` - inject the regular Angular $injector to retrieve service.

### Test Method
```
it("should return some data", function(){
    // simulate HTTP GET
    $httpBackend.whenGet('http://...')
        .respond(['val1', 'val2']);

    myService.getItems().then(function(response){
        expect(response.data).toEqual(['val1', [val2]]);
    });

    $httpBackend.flush();
});
```