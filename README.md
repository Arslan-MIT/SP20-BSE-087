import { StyleSheet, Text, View, FlatList } from 'react-native';
import React from 'react';
import apiCall from './ApiCall';

export default function App() {
  const bitcoinData = apiCall();

  return (
    <View style={styles.container}>
      <FlatList
        data={bitcoinData}
        keyExtractor={(index) => index.toString()}
        renderItem={({ item }) => (
          <View style={styles.itemContainer}>
            <Text style={styles.text}>Time: {item.time}</Text>
            <Text style={styles.text}>USD Rate: {item.usdRate}</Text>
          </View>
        )}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    marginTop: 50,
  },
  itemContainer: {
    padding: 16,
    borderBottomWidth: 1,
    borderBottomColor: '#ccc',
  },
  text: {
    fontSize: 18,
  },
});




