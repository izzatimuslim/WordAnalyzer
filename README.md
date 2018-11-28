import React, {Component} from 'react';
import {StyleSheet, Text, View, TextInput, Alert, Button, Image} from 'react-native';



export default class App extends Component{

  constructor(){
    super();
    this.state={
      word : '',
      arr: [],
      countCons: 0,
      countVow: 0,
      countChar: 0
     
    };
  }



AnalyzeWord= () => { 


  this.setState({countCons:0})
  this.setState({countVow:0})
  this.setState({countChar:0})
  
  this.setState({array:this.state.word.split("")},()=> {
      this.setState({countChar:this.state.array.length})

      for(var i = 0; i < this.state.array.length; i++){
        const checker=['a','e','i','o','u','A','E','I','O','U'];
        const letter = this.state.array[i];

        if(checker.includes(letter)){
          this.setState({countVow: this.state.countVow +=1})
        }

        else{
          this.setState({countCons:this.state.countCons +=1})
        }

      }
      
    }
  )};
  


render() {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>WORD ANALYZER</Text>
    
      <TextInput onChangeText={(word)=>this.setState({word})} placeholder="Key In Word"/>
      
      <Button onPress={() =>this.AnalyzeWord()} title="Analyze"></Button>
      <Text style={styles.contents}>Word:</Text> <Text style={styles.answers}>{this.state.word}</Text>

      <Text style={styles.contents}>No.of Consonants:</Text>
      <Text style={styles.answers}>{this.state.countCons}</Text>

      <Text style={styles.contents}>No. of Vowels:</Text>
      <Text style={styles.answers}>{this.state.countVow}</Text>

      <Text style={styles.contents}>No. of Characters:</Text>
      <Text style={styles.answers}>{this.state.countChar}</Text>

      
  </View>
  );
}
}

const styles = StyleSheet.create({
  container:{
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
    fontSize: 14,
  },

  title:{
    fontSize: 24,
    textAlign: 'center',
    margin: 10,

  },

  contents:{
    textAlign:'center',
    color: '#333333',
    marginBottom:5,
    fontSize:18

},

answers:{
  textAlign:'center',
    color: '#FF8C00',
    marginBottom:5,
    
    fontSize:17
}
}) 
