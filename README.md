# angularjs1-5-route-change-events
AngularJS 1.5 Route Change Events

Based on 'Route Change Events' at https://www.youtube.com/watch?v=tdIgsclQR6E&list=PL6n9fhu94yhWKHkcL7RJmmXyxkuFB3KSl&index=39&spfreload=1

#Route Change Events

##Different events are triggered when a route change occurs in an angular application.

When a route navigation occurs in an angular application, the following events are triggered:

1. $locationChangeStart
2. $routeChangeStart
3. $locationChangeSuccess
4. $routeChangeSuccess

##Logging the events, using ```$rootScope```.

```javascript
[...]
    .controller("studentsCtrl", function($http, $route, $rootScope, $log) {

        var vm = this;

        $rootScope.$on("$locationChangeStart", function() {
            $log.debug("$locationChangeStart fired");
        });

        $rootScope.$on("$routeChangeStart", function() {
            $log.debug("$rootChangeStart fired");
        });

        $rootScope.$on("$locationChangeSuccess", function() {
            $log.debug("$locationChangeSuccess fired");
        });

        $rootScope.$on("$routeChangeSuccess", function() {
            $log.debug("$rootChangeSuccess fired");
        });
        
        [...]
```

See scriptA.js, indexA.html and stylesA.css how to implement this.

##Logging the event handler parameters to inspect their respective properties, using ```$scope```.

```javascript
[...]
    .controller("studentsCtrl", function($http, $route, $scope, $log) {

        var vm = this;

        $scope.$on("$locationChangeStart", function(event, next, current) {
            $log.debug("$locationChangeStart fired");
            $log.debug("$locationChangeStart - event:");
            $log.debug(event);
            $log.debug("$locationChangeStart - next:");
            $log.debug(next);
            $log.debug("$locationChangeStart - current:");
            $log.debug(current);
        });

        $scope.$on("$routeChangeStart", function(event, next, current) {
            $log.debug("$rootChangeStart fired");
            $log.debug("$rootChangeStart - event:");
            $log.debug(event);
            $log.debug("$rootChangeStart - next:");
            $log.debug(next);
            $log.debug("$rootChangeStart - current:");
            $log.debug(current);
        });

        $scope.$on("$locationChangeSuccess", function(event, next, current) {
            $log.debug("$locationChangeSuccess fired");
            $log.debug("$locationChangeSuccess - event:");
            $log.debug(event);
            $log.debug("$locationChangeSuccess - next:");
            $log.debug(next);
            $log.debug("$locationChangeSuccess - current:");
            $log.debug(current);
        });

        $scope.$on("$routeChangeSuccess", function(event, next, current) {
            $log.debug("$rootChangeSuccess fired");
            $log.debug("$rootChangeSuccess - event:");
            $log.debug(event);
            $log.debug("$rootChangeSuccess - next:");
            $log.debug(next);
            $log.debug("$rootChangeSuccess - current:");
            $log.debug(current);
        });
        
        [...]
```

See scriptB.js, indexB.html and stylesB.css how to implement this.
