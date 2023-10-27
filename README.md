# CRUD GENERATOR . NET by emirhankarakoc
fastest rest api generator.
![crudfoto](https://github.com/emirhankarakoc/crudgenerator/assets/101813995/1002c19e-dfbd-48dd-8782-b41a581f1af1)

# DONT FORGET LIST
put your mouse cursor to your classname and add to your package, i cant detect from my computer :d you must replace it.

# put @Id and     @GeneratedValue(strategy = GenerationType.IDENTITY)
in Entity class

# add pomxml modelmapper and swagger
dependency:
```
		<dependency><groupId>org.springdoc</groupId><artifactId>springdoc-openapi-starter-webmvc-ui</artifactId><version>2.1.0</version></dependency>
		<dependency> <groupId>org.modelmapper</groupId><artifactId>modelmapper</artifactId> <version>3.1.1</version> </dependency>
```

## implemention codes:
Service:
```
  import org.modelmapper.ModelMapper;

    public interface ModelMapperService {
        ModelMapper forResponse();
        ModelMapper forRequest();
    }
```
Manager:
```

import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;
import org.modelmapper.ModelMapper;
import org.modelmapper.convention.MatchingStrategies;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
@Data
@AllArgsConstructor
@NoArgsConstructor
public class ModelMapperManager implements ModelMapperService{
    @Autowired
    private ModelMapper modelMapper;
    @Override
    public ModelMapper forResponse() {
        this.modelMapper.getConfiguration().setAmbiguityIgnored(true).setMatchingStrategy(MatchingStrategies.LOOSE);
        return this.modelMapper;
    }

    @Override
    public ModelMapper forRequest() {
        this.modelMapper.getConfiguration().setAmbiguityIgnored(true).setMatchingStrategy(MatchingStrategies.STANDARD);
        return this.modelMapper;
    }
}
```
# ENTITY NAME HAVE TO STARTS WITH UPPERCASE, CONTINUE WITH LOWERCASE. BE CAREFUL!
